---
title: "Konfigurowanie śledzenia przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bb64569984d71e35ef9f502c79d3a0bb8b4b8988
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="16edf-102">Konfigurowanie śledzenia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="16edf-102">Configuring Tracking for a Workflow</span></span>
<span data-ttu-id="16edf-103">Przepływ pracy można wykonać na trzy sposoby:</span><span class="sxs-lookup"><span data-stu-id="16edf-103">A workflow can execute in three ways:</span></span>  
  
-   <span data-ttu-id="16edf-104">Obsługiwane w<xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="16edf-104">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
-   <span data-ttu-id="16edf-105">Wykonane jako<xref:System.Activities.WorkflowApplication></span><span class="sxs-lookup"><span data-stu-id="16edf-105">Executed as a <xref:System.Activities.WorkflowApplication></span></span>  
  
-   <span data-ttu-id="16edf-106">Posługując się bezpośrednio<xref:System.Activities.WorkflowInvoker></span><span class="sxs-lookup"><span data-stu-id="16edf-106">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>  
  
 <span data-ttu-id="16edf-107">W zależności od opcji obsługi przepływu pracy można dodać uczestnika śledzenia za pośrednictwem kodu lub pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="16edf-107">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="16edf-108">W tym temacie opisano konfiguracji śledzenia, dodając śledzenie uczestnika do <xref:System.Activities.WorkflowApplication> i <xref:System.ServiceModel.Activities.WorkflowServiceHost>i jak włączyć śledzenie, korzystając z <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="16edf-108">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>  
  
## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="16edf-109">Konfigurowanie śledzenia aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="16edf-109">Configuring Workflow Application Tracking</span></span>  
 <span data-ttu-id="16edf-110">Przepływ pracy można uruchomić przy użyciu <xref:System.Activities.WorkflowApplication> klasy.</span><span class="sxs-lookup"><span data-stu-id="16edf-110">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="16edf-111">W tym temacie przedstawiono sposób śledzenia jest skonfigurowany dla [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] aplikacji przepływu pracy, dodając śledzenie uczestnika do <xref:System.Activities.WorkflowApplication> hosta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="16edf-111">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="16edf-112">W takim przypadku przepływ pracy jest uruchamiany jako aplikacja przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="16edf-112">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="16edf-113">Skonfigurować aplikację przepływu pracy za pomocą kodu (a nie przy użyciu pliku konfiguracji), który jest samodzielnie hostowana .exe plik za pomocą <xref:System.Activities.WorkflowApplication> klasy.</span><span class="sxs-lookup"><span data-stu-id="16edf-113">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="16edf-114">Uczestnik śledzenia jest dodawana jako rozszerzenie <xref:System.Activities.WorkflowApplication> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="16edf-114">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="16edf-115">Jest to realizowane przez dodanie <xref:System.Activities.Tracking.TrackingParticipant> do kolekcji rozszerzeń dla tego wystąpienia obiektu WorkflowApplication.</span><span class="sxs-lookup"><span data-stu-id="16edf-115">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>  
  
 <span data-ttu-id="16edf-116">W przypadku aplikacji przepływu pracy, można dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> rozszerzenia zachowania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="16edf-116">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>  
  
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
  
### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="16edf-117">Konfigurowanie śledzenia usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="16edf-117">Configuring Workflow Service Tracking</span></span>  
 <span data-ttu-id="16edf-118">Przepływ pracy może być udostępniany jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi, jeśli jest przeprowadzana w <xref:System.ServiceModel.Activities.WorkflowServiceHost> hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="16edf-118">A workflow can be exposed as a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="16edf-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost>to specjalne implementacja .NET ServiceHost dla usługi opartej na przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="16edf-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="16edf-120">W tej sekcji opisano sposób konfigurowania śledzenia dla [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] usługi przepływu pracy uruchomionych w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="16edf-120">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="16edf-121">Jest skonfigurowany za pomocą pliku Web.config (dla usługi sieci Web hostowanych) lub plik App.config (dla usługi hostowanej w autonomicznej aplikacji, na przykład aplikacji konsoli), określając zachowanie usługi lub za pomocą kodu dodając zachowanie specyficzne dla śledzenia w celu <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekcji hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="16edf-121">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>  
  
 <span data-ttu-id="16edf-122">Dla usługi przepływu pracy hostowanych w <xref:System.ServiceModel.WorkflowServiceHost>, możesz dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> przy użyciu <`behavior`> w pliku konfiguracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="16edf-122">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
```xml  
<behaviors>  
   <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile" />  
        </behavior>              
   </serviceBehaviors>  
<behaviors>  
```  
  
 <span data-ttu-id="16edf-123">Alternatywnie usługi przepływu pracy hostowanych w <xref:System.ServiceModel.WorkflowServiceHost>, możesz dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> rozszerzenia zachowania za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="16edf-123">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="16edf-124">Aby dodać niestandardowe śledzenia uczestnika, Utwórz nowe rozszerzenia zachowania i dodaj go do <xref:System.ServiceModel.ServiceHost> jak pokazano w poniższym przykładzie kodzie.</span><span class="sxs-lookup"><span data-stu-id="16edf-124">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16edf-125">Jeśli chcesz wyświetlić przykładowy kod, który pokazuje, jak utworzyć element zachowania niestandardowego, który dodaje uczestnika śledzenia niestandardowych, można skorzystać z [śledzenia](../../../docs/framework/windows-workflow-foundation/samples/tracking.md) próbek.</span><span class="sxs-lookup"><span data-stu-id="16edf-125">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>  
  
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
  
 <span data-ttu-id="16edf-126">Uczestnik śledzenia jest dodawany do hosta usługi przepływu pracy jako rozszerzenie do zachowania.</span><span class="sxs-lookup"><span data-stu-id="16edf-126">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>  
  
 <span data-ttu-id="16edf-127">Ten przykładowy kod poniżej pokazano, jak można odczytać z pliku konfiguracji profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="16edf-127">This sample code below shows how to read a tracking profile from configuration file.</span></span>  
  
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
  
 <span data-ttu-id="16edf-128">Ten przykładowy kod przedstawia sposób dodawania profilu śledzenia do hosta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="16edf-128">This sample code shows how to add a tracking profile to a workflow host.</span></span>  
  
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
>  <span data-ttu-id="16edf-129">Więcej informacji o śledzeniu profile, można znaleźć w [śledzenia profile](http://go.microsoft.com/fwlink/?LinkId=201310).</span><span class="sxs-lookup"><span data-stu-id="16edf-129">For more information on tracking profiles, refer to [Tracking Profiles](http://go.microsoft.com/fwlink/?LinkId=201310).</span></span>  
  
### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="16edf-130">Konfigurowanie śledzenia przy użyciu WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="16edf-130">Configuring tracking using WorkflowInvoker</span></span>  
 <span data-ttu-id="16edf-131">Aby skonfigurować śledzenia dla przepływu pracy wykonywane przy użyciu <xref:System.Activities.WorkflowInvoker>, Dodaj dostawcę śledzenia jako rozszerzenie <xref:System.Activities.WorkflowInvoker> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="16edf-131">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="16edf-132">Poniższy przykładowy kod jest z [śledzenia niestandardowe](../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="16edf-132">The following code example is from the [Custom Tracking](../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample.</span></span>  
  
```  
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());  
invoker.Extensions.Add(customTrackingParticipant);  
invoker.Invoke();  
```  
  
### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="16edf-133">Wyświetlanie rekordów w Podglądzie zdarzeń śledzenia</span><span class="sxs-lookup"><span data-stu-id="16edf-133">Viewing tracking records in Event Viewer</span></span>  
 <span data-ttu-id="16edf-134">Istnieją dwa dzienniki Podglądu zdarzeń szczególne znaczenie widoku, gdy śledzenie wykonywanie WF — analityczne dziennika i dzienników debugowania.</span><span class="sxs-lookup"><span data-stu-id="16edf-134">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="16edf-135">Zarówno znajdują się w usłudze Microsoft &#124; Windows &#124; Węzeł aplikacji serwera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16edf-135">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span>  <span data-ttu-id="16edf-136">Dzienniki w tej sekcji zawierają zdarzenia z jednej aplikacji zamiast zdarzenia, które mają wpływ na cały system.</span><span class="sxs-lookup"><span data-stu-id="16edf-136">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>  
  
 <span data-ttu-id="16edf-137">Debugowanie śledzenia są zapisywane w dzienniku debugowania.</span><span class="sxs-lookup"><span data-stu-id="16edf-137">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="16edf-138">Aby zbierać WF debugowania śledzenia zdarzeń w Podglądzie zdarzeń, włączyć dziennik debugowania.</span><span class="sxs-lookup"><span data-stu-id="16edf-138">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>  
  
1.  <span data-ttu-id="16edf-139">Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom.**</span><span class="sxs-lookup"><span data-stu-id="16edf-139">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="16edf-140">W oknie dialogowym Uruchamianie wpisz `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="16edf-140">In the Run dialog, type `eventvwr`.</span></span>  
  
2.  <span data-ttu-id="16edf-141">W oknie dialogowym Podgląd zdarzeń, rozwiń węzeł **Dzienniki aplikacji i usług** węzła.</span><span class="sxs-lookup"><span data-stu-id="16edf-141">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>  
  
3.  <span data-ttu-id="16edf-142">Rozwiń węzeł **Microsoft**, **Windows**, i **aplikacji serwerowych aplikacji** węzłów.</span><span class="sxs-lookup"><span data-stu-id="16edf-142">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>  
  
4.  <span data-ttu-id="16edf-143">Kliknij prawym przyciskiem myszy **debugowania** węźle **aplikacji serwerowych aplikacji** , a następnie wybierz węzeł **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="16edf-143">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>  
  
5.  <span data-ttu-id="16edf-144">Wykonanie włączone śledzenie aplikacji generowanie zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="16edf-144">Execute your tracing-enabled application to generate tracing events.</span></span>  
  
6.  <span data-ttu-id="16edf-145">Kliknij prawym przyciskiem myszy **debugowania** a następnie wybierz węzeł **odświeżania.**</span><span class="sxs-lookup"><span data-stu-id="16edf-145">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="16edf-146">Śledzenie zdarzeń powinny być widoczne w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="16edf-146">Tracing events should be visible in the center pane.</span></span>  
  
 <span data-ttu-id="16edf-147">WF 4 udostępnia uczestnika śledzenia, który zapisuje rekordy śledzenia w sesji usługi ETW (zdarzenia śledzenia dla systemu Windows).</span><span class="sxs-lookup"><span data-stu-id="16edf-147">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="16edf-148">Uczestnik śledzenia zdarzeń systemu Windows jest skonfigurowany przy użyciu profilu śledzenia, aby subskrybować śledzenie rekordów.</span><span class="sxs-lookup"><span data-stu-id="16edf-148">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span>  <span data-ttu-id="16edf-149">Gdy śledzenie jest włączone, śledzenie rejestruje błędy są emitowane do funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="16edf-149">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="16edf-150">ETW śledzenia zdarzeń (między zakres 100 113) odpowiadający emitowane przez uczestnika śledzenia funkcji ETW zdarzenia śledzenia są zapisywane w dzienniku analitycznych.</span><span class="sxs-lookup"><span data-stu-id="16edf-150">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>  
  
 <span data-ttu-id="16edf-151">Aby wyświetlić rekordy śledzenia, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="16edf-151">To view tracking records, follow these steps.</span></span>  
  
1.  <span data-ttu-id="16edf-152">Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom.**</span><span class="sxs-lookup"><span data-stu-id="16edf-152">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="16edf-153">W oknie dialogowym Uruchamianie wpisz `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="16edf-153">In the Run dialog, type `eventvwr`.</span></span>  
  
2.  <span data-ttu-id="16edf-154">W oknie dialogowym Podgląd zdarzeń, rozwiń węzeł **Dzienniki aplikacji i usług** węzła.</span><span class="sxs-lookup"><span data-stu-id="16edf-154">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>  
  
3.  <span data-ttu-id="16edf-155">Rozwiń węzeł **Microsoft**, **Windows**, i **aplikacji serwerowych aplikacji** węzłów.</span><span class="sxs-lookup"><span data-stu-id="16edf-155">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>  
  
4.  <span data-ttu-id="16edf-156">Kliknij prawym przyciskiem myszy **analityczne** węźle **aplikacji serwerowych aplikacji** , a następnie wybierz węzeł **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="16edf-156">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>  
  
5.  <span data-ttu-id="16edf-157">Wykonanie włączone śledzenie aplikacji do wygenerowania rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="16edf-157">Execute your tracking-enabled application to generate tracking records.</span></span>  
  
6.  <span data-ttu-id="16edf-158">Kliknij prawym przyciskiem myszy **analityczne** a następnie wybierz węzeł **odświeżania.**</span><span class="sxs-lookup"><span data-stu-id="16edf-158">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="16edf-159">Śledzenie rekordów powinny być widoczne w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="16edf-159">Tracking records should be visible in the center pane.</span></span>  
  
 <span data-ttu-id="16edf-160">Na poniższej ilustracji przedstawiono śledzenia zdarzeń w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="16edf-160">The following image shows tracking events in the event viewer.</span></span>  
  
 <span data-ttu-id="16edf-161">![Wyświetlanie podglądu zdarzeń śledzenia rekordów](../../../docs/framework/windows-workflow-foundation/media/trackingeventviewer.PNG "TrackingEventViewer")</span><span class="sxs-lookup"><span data-stu-id="16edf-161">![Event Viewer showing tracking records](../../../docs/framework/windows-workflow-foundation/media/trackingeventviewer.PNG "TrackingEventViewer")</span></span>  
  
### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="16edf-162">Rejestrowanie identyfikator dostawcy specyficzne dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="16edf-162">Registering an application-specific provider ID</span></span>  
 <span data-ttu-id="16edf-163">Jeśli zdarzeń muszą być zapisywane w dzienniku aplikacji, wykonaj następujące kroki, aby zarejestrować nowe manifestu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="16edf-163">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>  
  
1.  <span data-ttu-id="16edf-164">Deklarowanie identyfikator dostawcy w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16edf-164">Declare the provider ID in the application configuration file.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>  
    </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="16edf-165">Skopiuj plik manifestu z %windir%\Microsoft.NET\Framework\\< najnowszą wersję [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man do tymczasowej lokalizacji i zmień jego nazwę Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span><span class="sxs-lookup"><span data-stu-id="16edf-165">Copy the manifest file from %windir%\Microsoft.NET\Framework\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>  
  
3.  <span data-ttu-id="16edf-166">Zmień identyfikator GUID w pliku manifestu nowego identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="16edf-166">Change the GUID in the manifest file to the new GUID.</span></span>  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
4.  <span data-ttu-id="16edf-167">Zmień nazwę dostawcy, jeśli nie chcesz odinstalować domyślnego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="16edf-167">Change the provider name if you do not want to uninstall the default provider.</span></span>  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
5.  <span data-ttu-id="16edf-168">Jeśli zmienisz nazwę dostawcy w poprzednim kroku, należy zmienić nazwy kanału w pliku manifestu na nową nazwę dostawcy.</span><span class="sxs-lookup"><span data-stu-id="16edf-168">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>  
  
    ```xml  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />  
    ```  
  
6.  <span data-ttu-id="16edf-169">Generowanie biblioteki DLL zasobu, wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="16edf-169">Generate the resource DLL by following these steps.</span></span>  
  
    1.  <span data-ttu-id="16edf-170">Zainstaluj zestaw Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="16edf-170">Install the Windows SDK.</span></span> <span data-ttu-id="16edf-171">Zestaw SDK systemu Windows zawiera komunikat kompilatora ([mc.exe](http://go.microsoft.com/fwlink/?LinkId=184606)) i kompilatora zasobów ([rc.exe](http://go.microsoft.com/fwlink/?LinkId=184605)).</span><span class="sxs-lookup"><span data-stu-id="16edf-171">The Windows SDK includes the message compiler ([mc.exe](http://go.microsoft.com/fwlink/?LinkId=184606)) and resource compiler ([rc.exe](http://go.microsoft.com/fwlink/?LinkId=184605)).</span></span>  
  
    2.  <span data-ttu-id="16edf-172">W wierszu polecenia systemu Windows SDK należy uruchomić mc.exe na nowym pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="16edf-172">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>  
  
        ```  
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
    3.  <span data-ttu-id="16edf-173">Uruchom rc.exe na plik zasobów wygenerowany w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="16edf-173">Run rc.exe on the resource file generated in the previous step.</span></span>  
  
        ```  
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc  
        ```  
  
    4.  <span data-ttu-id="16edf-174">Utwórz cs pusty plik o nazwie NewProviderReg.cs.</span><span class="sxs-lookup"><span data-stu-id="16edf-174">Create an empty cs file called NewProviderReg.cs.</span></span>  
  
    5.  <span data-ttu-id="16edf-175">Utwórz zasób biblioteki DLL przy użyciu kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="16edf-175">Create a resource DLL using the C# compiler.</span></span>  
  
        ```  
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll  
        ```  
  
    6.  <span data-ttu-id="16edf-176">Zmień namel dl zasobów i komunikatów w pliku manifestu z `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` na nową nazwę biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="16edf-176">Change the resource and message dl namel in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>  
  
        ```xml  
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">  
        ```  
  
    7.  <span data-ttu-id="16edf-177">Użyj [wevtutil](http://go.microsoft.com/fwlink/?LinkId=184608) zarejestrować manifestu.</span><span class="sxs-lookup"><span data-stu-id="16edf-177">Use [wevtutil](http://go.microsoft.com/fwlink/?LinkId=184608) to register the manifest.</span></span>  
  
        ```  
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="16edf-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16edf-178">See Also</span></span>  
 [<span data-ttu-id="16edf-179">Windows Server AppFabric monitorowania</span><span class="sxs-lookup"><span data-stu-id="16edf-179">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="16edf-180">Monitorowanie aplikacji przy użyciu rozwiązania AppFabric</span><span class="sxs-lookup"><span data-stu-id="16edf-180">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
