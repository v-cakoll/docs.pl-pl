---
title: Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 101aab98a7d34ad45ad29efbe252cff0814ca290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185394"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="14d9c-102">Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania</span><span class="sxs-lookup"><span data-stu-id="14d9c-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="14d9c-103">Rozszerzenie <xref:System.ServiceModel.Activities.SendMessageChannelCache> umożliwia dostosowanie poziomów udostępniania pamięci podręcznej, ustawień pamięci podręcznej fabryki kanałów i ustawień pamięci podręcznej kanału dla <xref:System.ServiceModel.Activities.Send> przepływów pracy, które wysyłają wiadomości do punktów końcowych usługi przy użyciu działań obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="14d9c-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="14d9c-104">Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="14d9c-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="14d9c-105">Pamięć podręczna fabryki <xref:System.ServiceModel.ChannelFactory%601> kanałów zawiera obiekty buforowane.</span><span class="sxs-lookup"><span data-stu-id="14d9c-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="14d9c-106">Pamięć podręczna kanału zawiera buforowane kanały.</span><span class="sxs-lookup"><span data-stu-id="14d9c-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14d9c-107">Przepływy pracy <xref:System.ServiceModel.Activities.Send> mogą używać działań obsługi wiadomości do wysyłania wiadomości lub parametrów.</span><span class="sxs-lookup"><span data-stu-id="14d9c-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="14d9c-108">Środowisko wykonawcze przepływu pracy dodaje fabryki kanałów do <xref:System.ServiceModel.Channels.IRequestChannel> pamięci podręcznej, które tworzą kanały typu podczas używania <xref:System.ServiceModel.Activities.ReceiveReply> działania <xref:System.ServiceModel.Activities.Send> z działaniem, a <xref:System.ServiceModel.Channels.IOutputChannel> gdy po prostu przy użyciu <xref:System.ServiceModel.Activities.Send> działania (nie <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="14d9c-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="14d9c-109">Poziomy udostępniania pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="14d9c-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="14d9c-110">Domyślnie w przepływie pracy obsługiwanym przez pamięć podręczną używaną <xref:System.ServiceModel.WorkflowServiceHost> przez <xref:System.ServiceModel.Activities.Send> działania obsługi <xref:System.ServiceModel.WorkflowServiceHost> wiadomości jest współużytkowany przez wszystkie wystąpienia przepływu pracy w (buforowanie na poziomie hosta).</span><span class="sxs-lookup"><span data-stu-id="14d9c-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="14d9c-111">Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia).</span><span class="sxs-lookup"><span data-stu-id="14d9c-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="14d9c-112">Pamięć podręczna jest <xref:System.ServiceModel.Activities.Send> dostępna tylko dla działań, które nie używają punktów końcowych zdefiniowanych w konfiguracji, chyba że jest włączone buforowanie niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="14d9c-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="14d9c-113">Poniżej przedstawiono różne poziomy <xref:System.ServiceModel.Activities.Send> udostępniania pamięci podręcznej dostępne dla działań w przepływie pracy i ich zalecane użycie:</span><span class="sxs-lookup"><span data-stu-id="14d9c-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
- <span data-ttu-id="14d9c-114">**Poziom hosta:** Na poziomie udostępniania hosta pamięć podręczna jest dostępna tylko dla wystąpień przepływu pracy hostowanych na hoście usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="14d9c-115">Pamięć podręczna może być również współużytkowana między hostami usługi przepływu pracy w pamięci podręcznej całego procesu.</span><span class="sxs-lookup"><span data-stu-id="14d9c-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
- <span data-ttu-id="14d9c-116">**Poziom wystąpienia:** Na poziomie udostępniania wystąpienia pamięć podręczna jest dostępna dla określonego wystąpienia przepływu pracy przez cały okres jego istnienia, ale pamięć podręczna nie jest dostępna dla innych wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
- <span data-ttu-id="14d9c-117">**Brak pamięci podręcznej:** Pamięć podręczna jest domyślnie wyłączona, jeśli masz przepływ pracy, który używa punktów końcowych zdefiniowanych w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="14d9c-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="14d9c-118">Zaleca się również, aby zachować pamięć podręczną wyłączoną w tym przypadku, ponieważ włączenie jej może być niezabezpieczone.</span><span class="sxs-lookup"><span data-stu-id="14d9c-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="14d9c-119">Na przykład jeśli dla każdego wysyłania wymagana jest inna tożsamość (różne poświadczenia lub użycie personifikacji).</span><span class="sxs-lookup"><span data-stu-id="14d9c-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="14d9c-120">Zmiana poziomu udostępniania pamięci podręcznej dla przepływu pracy klienta</span><span class="sxs-lookup"><span data-stu-id="14d9c-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="14d9c-121">Aby ustawić udostępnianie pamięci podręcznej w przepływie <xref:System.ServiceModel.Activities.SendMessageChannelCache> pracy klienta, dodaj wystąpienie klasy jako rozszerzenie do żądanego zestawu wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="14d9c-122">Powoduje to udostępnianie pamięci podręcznej we wszystkich wystąpieniach przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="14d9c-123">Poniższe przykłady kodu pokazują, jak wykonać te kroki.</span><span class="sxs-lookup"><span data-stu-id="14d9c-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="14d9c-124">Najpierw zadeklaruj <xref:System.ServiceModel.Activities.SendMessageChannelCache>wystąpienie typu .</span><span class="sxs-lookup"><span data-stu-id="14d9c-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="14d9c-125">Następnie dodaj rozszerzenie pamięci podręcznej do każdego wystąpienia przepływu pracy klienta.</span><span class="sxs-lookup"><span data-stu-id="14d9c-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="14d9c-126">Zmiana poziomu udostępniania pamięci podręcznej dla usługi hostowanego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="14d9c-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="14d9c-127">Aby ustawić udostępnianie pamięci podręcznej w obsługiwanej usłudze <xref:System.ServiceModel.Activities.SendMessageChannelCache> przepływu pracy, dodaj wystąpienie klasy jako rozszerzenie do wszystkich hostów usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="14d9c-128">Powoduje to udostępnianie pamięci podręcznej we wszystkich hostach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="14d9c-129">Poniższe przykłady kodu pokazują, aby wykonać te kroki.</span><span class="sxs-lookup"><span data-stu-id="14d9c-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="14d9c-130">Najpierw zadeklarować wystąpienie <xref:System.ServiceModel.Activities.SendMessageChannelCache> typu na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="14d9c-131">Następnie dodaj statyczne rozszerzenie pamięci podręcznej do każdego hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="14d9c-132">Aby ustawić udostępnianie pamięci podręcznej w hostowanej usłudze `Func<SendMessageChannelCache>` przepływu pracy na poziomie wystąpienia, dodaj pełnomocnika jako rozszerzenie do hosta usługi <xref:System.ServiceModel.Activities.SendMessageChannelCache> przepływu pracy i przypisz tego pełnomocnika do kodu, który powoduje utworzenie nowego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="14d9c-133">Powoduje to inną pamięć podręczną dla każdego wystąpienia przepływu pracy, a nie pojedynczą pamięć podręczną współużytkowaną przez wszystkie wystąpienia przepływu pracy w hoście usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="14d9c-134">Poniższy przykład kodu pokazuje, jak to osiągnąć za pomocą wyrażenia <xref:System.ServiceModel.Activities.SendMessageChannelCache> lambda, aby bezpośrednio zdefiniować rozszerzenie, które wskazuje delegata.</span><span class="sxs-lookup"><span data-stu-id="14d9c-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
```csharp
serviceHost.WorkflowExtensions.Add(() => new SendMessageChannelCache  
{  
    // Use FactorySettings property to add custom factory cache settings.  
    FactorySettings = new ChannelCacheSettings
    { MaxItemsInCache = 5, },  
    // Use ChannelSettings property to add custom channel cache settings.  
    ChannelSettings = new ChannelCacheSettings
    { MaxItemsInCache = 10 },  
});  
```  
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="14d9c-135">Dostosowywanie ustawień pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="14d9c-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="14d9c-136">Można dostosować ustawienia pamięci podręcznej dla pamięci podręcznej fabryki kanałów i pamięci podręcznej kanału.</span><span class="sxs-lookup"><span data-stu-id="14d9c-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="14d9c-137">Ustawienia pamięci podręcznej <xref:System.ServiceModel.Activities.ChannelCacheSettings> są zdefiniowane w klasie.</span><span class="sxs-lookup"><span data-stu-id="14d9c-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="14d9c-138">Klasa <xref:System.ServiceModel.Activities.SendMessageChannelCache> definiuje domyślne ustawienia pamięci podręcznej pamięci podręcznej fabryki kanałów i pamięci podręcznej kanału w konstruktorze bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="14d9c-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its parameterless constructor.</span></span> <span data-ttu-id="14d9c-139">W poniższej tabeli wymieniono wartości domyślne tych ustawień pamięci podręcznej dla każdego typu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="14d9c-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="14d9c-140">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="14d9c-140">Settings</span></span>|<span data-ttu-id="14d9c-141">LeaseTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="14d9c-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="14d9c-142">Czas bezczynny (min)</span><span class="sxs-lookup"><span data-stu-id="14d9c-142">IdleTimeout (min)</span></span>|<span data-ttu-id="14d9c-143">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="14d9c-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="14d9c-144">Domyślna pamięć podręczna fabryki</span><span class="sxs-lookup"><span data-stu-id="14d9c-144">Factory Cache Default</span></span>|<span data-ttu-id="14d9c-145">TimeSpan.MaxValue</span><span class="sxs-lookup"><span data-stu-id="14d9c-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="14d9c-146">2</span><span class="sxs-lookup"><span data-stu-id="14d9c-146">2</span></span>|<span data-ttu-id="14d9c-147">16</span><span class="sxs-lookup"><span data-stu-id="14d9c-147">16</span></span>|  
|<span data-ttu-id="14d9c-148">Domyślna pamięć podręczna kanału</span><span class="sxs-lookup"><span data-stu-id="14d9c-148">Channel Cache Default</span></span>|<span data-ttu-id="14d9c-149">5</span><span class="sxs-lookup"><span data-stu-id="14d9c-149">5</span></span>|<span data-ttu-id="14d9c-150">2</span><span class="sxs-lookup"><span data-stu-id="14d9c-150">2</span></span>|<span data-ttu-id="14d9c-151">16</span><span class="sxs-lookup"><span data-stu-id="14d9c-151">16</span></span>|  
  
 <span data-ttu-id="14d9c-152">Aby dostosować ustawienia pamięci podręcznej i pamięci <xref:System.ServiceModel.Activities.SendMessageChannelCache> podręcznej kanału, wystąpienia <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> klasy przy użyciu <xref:System.ServiceModel.Activities.ChannelCacheSettings> konstruktora sparametryzowanego i przekazać nowe wystąpienie z wartościami niestandardowymi do każdego z `factorySettings` parametrów i. `channelSettings`</span><span class="sxs-lookup"><span data-stu-id="14d9c-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="14d9c-153">Następnie dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy lub wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="14d9c-154">W poniższym przykładzie kodu pokazano, jak wykonać te kroki dla wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(5),
                        LeaseTimeout = TimeSpan.FromMinutes(20)};  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(2),  
                        LeaseTimeout = TimeSpan.FromMinutes(10) };  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="14d9c-155">Aby włączyć buforowanie, gdy usługa przepływu pracy ma punkty końcowe <xref:System.ServiceModel.Activities.SendMessageChannelCache> zdefiniowane w konfiguracji, wystąpienia klasy przy użyciu konstruktora <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> sparametryzowanego z parametrem ustawionym `allowUnsafeCaching` na `true`.</span><span class="sxs-lookup"><span data-stu-id="14d9c-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="14d9c-156">Następnie dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy lub wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="14d9c-157">W poniższym przykładzie kodu pokazano, jak włączyć buforowanie dla wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14d9c-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="14d9c-158">Aby całkowicie wyłączyć pamięć podręczną dla fabryk kanałów i kanałów, należy wyłączyć pamięć podręczną fabryki kanałów.</span><span class="sxs-lookup"><span data-stu-id="14d9c-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="14d9c-159">W ten sposób wyłącza również pamięć podręczną kanału, ponieważ kanały są własnością odpowiednich fabryk kanałów.</span><span class="sxs-lookup"><span data-stu-id="14d9c-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="14d9c-160">Aby wyłączyć pamięć podręczną `factorySettings` fabryki kanału, należy przekazać parametr do <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> konstruktora zainicjowanego do <xref:System.ServiceModel.Activities.ChannelCacheSettings> wystąpienia o <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> wartości 0.</span><span class="sxs-lookup"><span data-stu-id="14d9c-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="14d9c-161">Poniższy przykład kodu pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="14d9c-161">The following code example shows this.</span></span>  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="14d9c-162">Można użyć tylko pamięci podręcznej fabryki kanału i wyłączyć `channelSettings` pamięć <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> podręczną kanału, <xref:System.ServiceModel.Activities.ChannelCacheSettings> przekazując <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> parametr do konstruktora zainicjowanego do wystąpienia o wartości 0.</span><span class="sxs-lookup"><span data-stu-id="14d9c-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="14d9c-163">Poniższy przykład kodu pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="14d9c-163">The following code example shows this.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="14d9c-164">W obsługiwanej usłudze przepływu pracy można określić ustawienia pamięci podręcznej i pamięci podręcznej kanału w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="14d9c-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="14d9c-165">W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą.</span><span class="sxs-lookup"><span data-stu-id="14d9c-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="14d9c-166">W poniższym przykładzie przedstawiono zawartość `MyChannelCacheBehavior` pliku konfiguracyjnego, który zawiera zachowanie usługi z niestandardowymi ustawieniami pamięci podręcznej fabryki i pamięci podręcznej kanału.</span><span class="sxs-lookup"><span data-stu-id="14d9c-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="14d9c-167">To zachowanie usługi jest dodawany `behaviorConfiguration` do usługi za pośrednictwem atrybutu.</span><span class="sxs-lookup"><span data-stu-id="14d9c-167">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>  
    <!-- List of other config sections here -->
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```
