---
title: Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: e439edc14183c2ba2bf9af67e177dddb52c43708
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784296"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="6f7e0-102">Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania</span><span class="sxs-lookup"><span data-stu-id="6f7e0-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="6f7e0-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Rozszerzenie umożliwia dostosowywania pamięci podręcznej udostępnianie poziomy, ustawienia pamięci podręcznej fabryki kanału i ustawień kanału pamięci podręcznej dla przepływów pracy, który wysyła wiadomości do punktów końcowych usługi za pomocą <xref:System.ServiceModel.Activities.Send> działań dotyczących komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="6f7e0-104">Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="6f7e0-105">Zawiera pamięci podręcznej fabryki kanału pamięci podręcznej <xref:System.ServiceModel.ChannelFactory%601> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="6f7e0-106">Pamięci podręcznej kanału zawiera kanały pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f7e0-107">Przepływy pracy można użyć <xref:System.ServiceModel.Activities.Send> wiadomości działania na wysyłanie wiadomości lub parametrów.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="6f7e0-108">Środowiska wykonawczego przepływów pracy, dodaje fabryki kanałów do pamięci podręcznej, którą tworzyć kanały typu <xref:System.ServiceModel.Channels.IRequestChannel> zastosowania <xref:System.ServiceModel.Activities.ReceiveReply> działanie przy użyciu <xref:System.ServiceModel.Activities.Send> działania i <xref:System.ServiceModel.Channels.IOutputChannel> korzystając tylko <xref:System.ServiceModel.Activities.Send> działania (nie <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="6f7e0-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="6f7e0-109">Poziomów współużytkowania pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="6f7e0-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="6f7e0-110">Domyślnie w przepływie pracy pracujących <xref:System.ServiceModel.WorkflowServiceHost> pamięci podręcznej używanej przez <xref:System.ServiceModel.Activities.Send> działań dotyczących komunikatów jest współużytkowany przez wszystkie wystąpienia przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> (host poziomie buforowania).</span><span class="sxs-lookup"><span data-stu-id="6f7e0-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="6f7e0-111">Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia).</span><span class="sxs-lookup"><span data-stu-id="6f7e0-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="6f7e0-112">Pamięć podręczna jest dostępna tylko dla <xref:System.ServiceModel.Activities.Send> działań, które nie korzystają z punktów końcowych zdefiniowanych w konfiguracji, o ile nie jest włączone buforowanie niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="6f7e0-113">Oto różnych pamięci podręcznej udostępnianie poziomy dostępne dla <xref:System.ServiceModel.Activities.Send> działania w przepływie pracy oraz ich zalecane użycie:</span><span class="sxs-lookup"><span data-stu-id="6f7e0-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
- <span data-ttu-id="6f7e0-114">**Hostowanie poziom**: Na hoście, poziomu udostępniania pamięć podręczna jest dostępna tylko dla wystąpienia przepływu pracy, hostowana w hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="6f7e0-115">Pamięć podręczna również mogą być współużytkowane między hostami usługi przepływu pracy w pamięci podręcznej całego procesu.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
- <span data-ttu-id="6f7e0-116">**Wystąpienie poziomu**: W wystąpieniu, poziomu udostępniania, pamięć podręczna jest dostępna dla wystąpienia określonego przepływu pracy, w okresie swojego istnienia, ale pamięci podręcznej nie jest dostępna dla innych wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
- <span data-ttu-id="6f7e0-117">**Brak pamięci podręcznej**: Pamięć podręczna jest domyślnie wyłączona w przypadku przepływu pracy, który używa punktów końcowych zdefiniowanych w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="6f7e0-118">Zalecane jest także zachowywać pamięci podręcznej wyłączone w tym przypadku, ponieważ jej włączeniu, może być niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="6f7e0-119">Na przykład w przypadku określenia innej tożsamości (inne poświadczenia lub korzystanie z personifikacji) jest wymagana dla każdego wysyłania.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="6f7e0-120">Zmienianie poziomu udostępniania dla przepływu pracy klienta pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="6f7e0-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="6f7e0-121">Aby ustawić pamięci podręcznej udostępnianie w przepływie pracy klienta, należy dodać wystąpienia <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy jako rozszerzenie dla żądanej grupy wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="6f7e0-122">Powoduje to udostępnianie pamięci podręcznej przez wszystkie wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="6f7e0-123">W poniższych przykładach kodu pokazano, jak wykonać te kroki.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="6f7e0-124">Najpierw należy zadeklarować wystąpienia typu <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="6f7e0-125">Następnie dodaj rozszerzenie pamięci podręcznej do każdego wystąpienia przepływu pracy klienta.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```csharp 
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="6f7e0-126">Zmienianie poziomu udostępniania w usłudze hostowanej przepływu pracy w pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="6f7e0-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="6f7e0-127">Aby ustawić pamięci podręcznej udostępnianie w usłudze hostowanej przepływu pracy, dodaje wystąpienie <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy jako rozszerzenie dla wszystkich hostów usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="6f7e0-128">Powoduje to udostępnianie pamięci podręcznej na wszystkich hostach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="6f7e0-129">W poniższych przykładach kodu pokazano wykonania tych kroków.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="6f7e0-130">Najpierw należy zadeklarować wystąpienia typu <xref:System.ServiceModel.Activities.SendMessageChannelCache> na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="6f7e0-131">Następnie dodaj rozszerzenie statycznej pamięci podręcznej do każdego hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="6f7e0-132">Aby ustawić udostępnianie w usłudze hostowanej przepływu pracy na poziomie wystąpienia pamięci podręcznej, należy dodać `Func<SendMessageChannelCache>` delegować jako rozszerzenie hosta usługi przepływu pracy i Przypisz ten delegat do kodu, który tworzy nowe wystąpienie klasy <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="6f7e0-133">Skutkuje to różne pamięci podręcznej dla każdego wystąpienia określonego przepływu pracy zamiast jednej pamięci podręcznej współużytkowane przez wszystkie wystąpienia przepływu pracy w hoście usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="6f7e0-134">Poniższy przykład kodu pokazuje, jak to osiągnąć przy użyciu wyrażenia lambda do definiowania bezpośrednio <xref:System.ServiceModel.Activities.SendMessageChannelCache> rozszerzenia, które wskazuje delegata.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
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
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="6f7e0-135">Dostosowywanie ustawień pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="6f7e0-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="6f7e0-136">Można dostosować ustawienia pamięci podręcznej dla pamięci podręcznej fabryki kanału i pamięci podręcznej kanału.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="6f7e0-137">Ustawienia pamięci podręcznej są zdefiniowane w <xref:System.ServiceModel.Activities.ChannelCacheSettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="6f7e0-138"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Klasa definiuje domyślnych ustawień pamięci podręcznej dla pamięci podręcznej fabryki kanału i pamięci podręcznej kanału w jej konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its default constructor.</span></span> <span data-ttu-id="6f7e0-139">W poniższej tabeli wymieniono wartości domyślne tych ustawień pamięci podręcznej dla każdego typu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="6f7e0-140">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="6f7e0-140">Settings</span></span>|<span data-ttu-id="6f7e0-141">LeaseTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="6f7e0-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="6f7e0-142">IdleTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="6f7e0-142">IdleTimeout (min)</span></span>|<span data-ttu-id="6f7e0-143">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="6f7e0-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="6f7e0-144">Domyślne pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="6f7e0-144">Factory Cache Default</span></span>|<span data-ttu-id="6f7e0-145">TimeSpan.MaxValue</span><span class="sxs-lookup"><span data-stu-id="6f7e0-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="6f7e0-146">2</span><span class="sxs-lookup"><span data-stu-id="6f7e0-146">2</span></span>|<span data-ttu-id="6f7e0-147">16</span><span class="sxs-lookup"><span data-stu-id="6f7e0-147">16</span></span>|  
|<span data-ttu-id="6f7e0-148">Domyślna pamięci podręcznej kanału</span><span class="sxs-lookup"><span data-stu-id="6f7e0-148">Channel Cache Default</span></span>|<span data-ttu-id="6f7e0-149">5</span><span class="sxs-lookup"><span data-stu-id="6f7e0-149">5</span></span>|<span data-ttu-id="6f7e0-150">2</span><span class="sxs-lookup"><span data-stu-id="6f7e0-150">2</span></span>|<span data-ttu-id="6f7e0-151">16</span><span class="sxs-lookup"><span data-stu-id="6f7e0-151">16</span></span>|  
  
 <span data-ttu-id="6f7e0-152">Aby dostosować ustawienia pamięci podręcznej pamięci podręcznej i kanał fabryki, utworzyć <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy za pomocą sparametryzowanego konstruktora <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> i przekazać nowe wystąpienie klasy <xref:System.ServiceModel.Activities.ChannelCacheSettings> przy użyciu niestandardowej wartości do poszczególnych `factorySettings` i `channelSettings` Parametry.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="6f7e0-153">Następnie dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy i wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="6f7e0-154">W poniższym przykładzie kodu pokazano, jak wykonać te kroki dla wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
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
  
 <span data-ttu-id="6f7e0-155">Aby włączyć buforowanie, gdy usługa przepływu pracy ma punktów końcowych zdefiniowanych w konfiguracji, tworzenia wystąpienia <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy za pomocą sparametryzowanego konstruktora <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> z `allowUnsafeCaching` parametr `true`.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="6f7e0-156">Następnie dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy i wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="6f7e0-157">Poniższy przykład kodu pokazuje, jak włączyć buforowanie dla wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="6f7e0-158">Aby wyłączyć pamięć podręczną całkowicie dla fabryki kanałów i kanały, należy wyłączyć pamięci podręcznej fabryki kanału.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="6f7e0-159">Również sposób powoduje wyłączenie pamięci podręcznej kanału, jak te kanały są własnością ich odpowiednich fabryki kanałów.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="6f7e0-160">Aby wyłączyć pamięci podręcznej fabryki kanału, należy przekazać `factorySettings` parametru, aby <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> Konstruktor inicjowany do <xref:System.ServiceModel.Activities.ChannelCacheSettings> wystąpienia z <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> wartość 0.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="6f7e0-161">Poniższy przykład kodu pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-161">The following code example shows this.</span></span>  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="6f7e0-162">Użytkownik może korzystać tylko cache fabryki kanałów i wyłączanie pamięci podręcznej kanału, przekazując `channelSettings` parametr <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> inicjowane Konstruktor <xref:System.ServiceModel.Activities.ChannelCacheSettings> wystąpienia z <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> wartość 0.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="6f7e0-163">Poniższy przykład kodu pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-163">The following code example shows this.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="6f7e0-164">W usłudze hostowanej przepływu pracy można określić fabryki pamięci podręcznej i kanał ustawienia pamięci podręcznej w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="6f7e0-165">W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="6f7e0-166">W poniższym przykładzie pokazano zawartość pliku konfiguracji, który zawiera `MyChannelCacheBehavior` usługi zachowanie przy użyciu ustawień pamięci podręcznej pamięci podręcznej i kanał fabrycznej.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="6f7e0-167">To zachowanie usługi jest dodawany do usługi za pośrednictwem `behaviorConfiguarion` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6f7e0-167">This service behavior is added to the service through the `behaviorConfiguarion` attribute.</span></span>  
  
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
