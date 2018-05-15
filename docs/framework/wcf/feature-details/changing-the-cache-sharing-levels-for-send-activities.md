---
title: Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 359a9189cee34eeb814a2303be3d2da725456e39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="6e92d-102">Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania</span><span class="sxs-lookup"><span data-stu-id="6e92d-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="6e92d-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Rozszerzenia umożliwia dostosowanie pamięci podręcznej udostępnianie poziomy, ustawienia pamięci podręcznej fabryki kanału i ustawienia kanału pamięci podręcznej dla przepływów pracy, który wysyła wiadomości do punktów końcowych usługi przy użyciu <xref:System.ServiceModel.Activities.Send> działań dotyczących komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6e92d-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="6e92d-104">Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="6e92d-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="6e92d-105">Pamięć podręczna fabryki kanału zawiera buforowane <xref:System.ServiceModel.ChannelFactory%601> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6e92d-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="6e92d-106">Pamięć podręczna kanału zawiera kanałów z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6e92d-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e92d-107">Przepływy pracy można użyć <xref:System.ServiceModel.Activities.Send> wiadomości działań do wysyłania wiadomości lub parametrów.</span><span class="sxs-lookup"><span data-stu-id="6e92d-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="6e92d-108">Środowiska uruchomieniowego przepływu pracy, dodaje fabryk kanałów, które do pamięci podręcznej, która tworzenia kanałów typu <xref:System.ServiceModel.Channels.IRequestChannel> korzystając <xref:System.ServiceModel.Activities.ReceiveReply> działania o <xref:System.ServiceModel.Activities.Send> działania i <xref:System.ServiceModel.Channels.IOutputChannel> używając po prostu <xref:System.ServiceModel.Activities.Send> działania (nie <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="6e92d-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="6e92d-109">Poziomów współużytkowania pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="6e92d-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="6e92d-110">Domyślnie w przepływie pracy obsługiwanych przez <xref:System.ServiceModel.WorkflowServiceHost> używanych przez pamięć podręczną <xref:System.ServiceModel.Activities.Send> działań dotyczących komunikatów jest współużytkowana przez wszystkie wystąpienia przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> (buforowanie hosta level).</span><span class="sxs-lookup"><span data-stu-id="6e92d-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="6e92d-111">Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia).</span><span class="sxs-lookup"><span data-stu-id="6e92d-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="6e92d-112">Pamięć podręczna jest dostępna tylko dla <xref:System.ServiceModel.Activities.Send> działania, które nie należy używać punktach końcowych zdefiniowanych w konfiguracji, chyba że jest włączone buforowanie niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="6e92d-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="6e92d-113">Poniżej przedstawiono różne pamięci podręcznej udostępnianie dostępnych dla poziomów <xref:System.ServiceModel.Activities.Send> działań w przepływie pracy oraz ich zalecane użycie:</span><span class="sxs-lookup"><span data-stu-id="6e92d-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
-   <span data-ttu-id="6e92d-114">**Host poziom**: na hoście poziomu udostępniania pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy w hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6e92d-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="6e92d-115">Pamięć podręczna również może być udostępniane między hostami usługi przepływu pracy w pamięci podręcznej całego procesu.</span><span class="sxs-lookup"><span data-stu-id="6e92d-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
-   <span data-ttu-id="6e92d-116">**Wystąpienie poziomu**: W przypadku poziomu udostępniania, jest dostępna do wystąpienia określonego przepływu pracy przez jego okres istnienia pamięci podręcznej, ale pamięci podręcznej nie jest dostępna dla innych wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6e92d-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
-   <span data-ttu-id="6e92d-117">**Brak pamięci podręcznej**: pamięci podręcznej jest domyślnie wyłączona w przypadku przepływu pracy korzystającego z punktów końcowych zdefiniowanych w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6e92d-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="6e92d-118">Zalecane jest również przechowywać w pamięci podręcznej wyłączone w tym przypadku ponieważ jej włączeniu, może być niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="6e92d-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="6e92d-119">Na przykład, jeśli inną tożsamość (inne poświadczenia lub korzystanie z personifikacji) jest wymagane dla każdego wysyłania.</span><span class="sxs-lookup"><span data-stu-id="6e92d-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="6e92d-120">Zmiana poziomu udostępniania dla przepływu pracy klienta pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="6e92d-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="6e92d-121">Aby skonfigurować udostępnianie w przepływie pracy klienta pamięci podręcznej, należy dodać wystąpienia <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy do żądany zestaw wystąpień przepływów pracy jako rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="6e92d-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="6e92d-122">Powoduje to udostępnianie pamięci podręcznej dla wszystkich wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6e92d-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="6e92d-123">W poniższych przykładach kodu pokazano, jak wykonać następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="6e92d-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="6e92d-124">Najpierw należy zadeklarować wystąpienia typu <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span><span class="sxs-lookup"><span data-stu-id="6e92d-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="6e92d-125">Następnie dodaj rozszerzenie pamięci podręcznej do każdego wystąpienia przepływu pracy klienta.</span><span class="sxs-lookup"><span data-stu-id="6e92d-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```  
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="6e92d-126">Zmiana pamięci podręcznej, poziomu udostępniania dla usługi hostowanej przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6e92d-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="6e92d-127">Aby ustawić pamięci podręcznej udostępnianie w usłudze hostowanej przepływu pracy, dodaje wystąpienie <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy do wszystkich hostów usługi przepływu pracy jako rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="6e92d-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="6e92d-128">Powoduje to udostępnianie pamięci podręcznej na wszystkich hostach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6e92d-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="6e92d-129">W poniższych przykładach kodu pokazano do wykonania tych kroków.</span><span class="sxs-lookup"><span data-stu-id="6e92d-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="6e92d-130">Najpierw należy zadeklarować wystąpienia typu <xref:System.ServiceModel.Activities.SendMessageChannelCache> na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="6e92d-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="6e92d-131">Następnie dodaj rozszerzenie statycznej pamięci podręcznej do każdego hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6e92d-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="6e92d-132">Aby skonfigurować udostępnianie w usłudze hostowanej przepływu pracy na poziomie wystąpienia pamięci podręcznej, należy dodać `Func<SendMessageChannelCache>` delegować do hosta usługi przepływu pracy jako rozszerzenie i Przypisz ten delegat do kodu, który tworzy nowe wystąpienie klasy <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="6e92d-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="6e92d-133">Powoduje to różnych pamięci podręcznej dla każdego wystąpienia przepływu pracy zamiast jednej pamięci podręcznej, współużytkowana przez wszystkie wystąpienia przepływu pracy z hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6e92d-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="6e92d-134">Poniższy przykład kodu pokazuje, jak to osiągnąć za pomocą wyrażenia lambda do definiowania bezpośrednio <xref:System.ServiceModel.Activities.SendMessageChannelCache> rozszerzenia, które wskazuje delegata.</span><span class="sxs-lookup"><span data-stu-id="6e92d-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
```  
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
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="6e92d-135">Dostosowywanie ustawień pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="6e92d-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="6e92d-136">Można dostosować ustawienia pamięci podręcznej pamięci podręcznej fabryki kanału i pamięci podręcznej kanału.</span><span class="sxs-lookup"><span data-stu-id="6e92d-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="6e92d-137">Ustawienia pamięci podręcznej są definiowane w <xref:System.ServiceModel.Activities.ChannelCacheSettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="6e92d-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="6e92d-138"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Klasa definiuje domyślnych ustawień pamięci podręcznej dla pamięci podręcznej fabryki kanału i pamięci podręcznej kanału w jego domyślny konstruktor.</span><span class="sxs-lookup"><span data-stu-id="6e92d-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its default constructor.</span></span> <span data-ttu-id="6e92d-139">W poniższej tabeli wymieniono wartości domyślne tych ustawień pamięci podręcznej dla każdego typu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6e92d-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="6e92d-140">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="6e92d-140">Settings</span></span>|<span data-ttu-id="6e92d-141">LeaseTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="6e92d-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="6e92d-142">IdleTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="6e92d-142">IdleTimeout (min)</span></span>|<span data-ttu-id="6e92d-143">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="6e92d-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="6e92d-144">Ustawienia fabryczne pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="6e92d-144">Factory Cache Default</span></span>|<span data-ttu-id="6e92d-145">Wartość TimeSpan.MaxValue</span><span class="sxs-lookup"><span data-stu-id="6e92d-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="6e92d-146">2</span><span class="sxs-lookup"><span data-stu-id="6e92d-146">2</span></span>|<span data-ttu-id="6e92d-147">16</span><span class="sxs-lookup"><span data-stu-id="6e92d-147">16</span></span>|  
|<span data-ttu-id="6e92d-148">Domyślna pamięci podręcznej kanału</span><span class="sxs-lookup"><span data-stu-id="6e92d-148">Channel Cache Default</span></span>|<span data-ttu-id="6e92d-149">5</span><span class="sxs-lookup"><span data-stu-id="6e92d-149">5</span></span>|<span data-ttu-id="6e92d-150">2</span><span class="sxs-lookup"><span data-stu-id="6e92d-150">2</span></span>|<span data-ttu-id="6e92d-151">16</span><span class="sxs-lookup"><span data-stu-id="6e92d-151">16</span></span>|  
  
 <span data-ttu-id="6e92d-152">Aby dostosować ustawienia pamięci podręcznej pamięci podręcznej i kanał fabryki, wystąpienia <xref:System.ServiceModel.Activities.SendMessageChannelCache> przy użyciu sparametryzowanym konstruktorze <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> i przekaż nowe wystąpienie klasy <xref:System.ServiceModel.Activities.ChannelCacheSettings> z wartościami niestandardowymi wszystkie `factorySettings` i `channelSettings` Parametry.</span><span class="sxs-lookup"><span data-stu-id="6e92d-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="6e92d-153">Następnie dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy i wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6e92d-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="6e92d-154">Poniższy przykład kodu pokazuje sposób wykonać te czynności dla wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6e92d-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
```  
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
  
 <span data-ttu-id="6e92d-155">Aby włączyć buforowanie w punktach końcowych zdefiniowanych w konfiguracji ma usługi przepływu pracy, należy utworzyć wystąpienia <xref:System.ServiceModel.Activities.SendMessageChannelCache> przy użyciu sparametryzowanym konstruktorze <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> z `allowUnsafeCaching` ustawiono parametr `true`.</span><span class="sxs-lookup"><span data-stu-id="6e92d-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="6e92d-156">Następnie dodaj nowe wystąpienie tej klasy jako rozszerzenie do hosta usługi przepływu pracy i wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6e92d-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="6e92d-157">Poniższy przykład kodu pokazuje, jak można włączyć buforowanie dla wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6e92d-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="6e92d-158">Aby wyłączyć w pamięci podręcznej całkowicie fabryk kanałów i kanały, należy wyłączyć pamięci podręcznej fabryki kanału.</span><span class="sxs-lookup"><span data-stu-id="6e92d-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="6e92d-159">Również w ten sposób powoduje wyłączenie pamięci podręcznej kanału, jak kanały są własnością ich odpowiednich fabryk kanałów.</span><span class="sxs-lookup"><span data-stu-id="6e92d-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="6e92d-160">Aby wyłączyć pamięci podręcznej fabryki kanału, należy przekazać `factorySettings` parametr <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> zainicjowany konstruktor <xref:System.ServiceModel.Activities.ChannelCacheSettings> wystąpienia z <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> wartość 0.</span><span class="sxs-lookup"><span data-stu-id="6e92d-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="6e92d-161">Poniższy przykład kodu pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="6e92d-161">The following code example shows this.</span></span>  
  
```  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="6e92d-162">Można użyć tylko bufor fabryki kanału i wyłączenie pamięci podręcznej kanału przekazując `channelSettings` parametr <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> zainicjowany konstruktor <xref:System.ServiceModel.Activities.ChannelCacheSettings> wystąpienia z <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> wartość 0.</span><span class="sxs-lookup"><span data-stu-id="6e92d-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="6e92d-163">Poniższy przykład kodu pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="6e92d-163">The following code example shows this.</span></span>  
  
```  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="6e92d-164">W usłudze hostowanej przepływu pracy można określić fabrykę pamięci podręcznej i kanał ustawienia pamięci podręcznej w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6e92d-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="6e92d-165">W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą.</span><span class="sxs-lookup"><span data-stu-id="6e92d-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="6e92d-166">W poniższym przykładzie pokazano zawartość pliku konfiguracji, który zawiera `MyChannelCacheBehavior` zachowania usługi przy użyciu ustawień pamięci podręcznej pamięci podręcznej i kanał fabrycznej.</span><span class="sxs-lookup"><span data-stu-id="6e92d-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="6e92d-167">To zachowanie usługi zostanie dodany do usługi za pośrednictwem `behaviorConfiguarion` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6e92d-167">This service behavior is added to the service through the `behaviorConfiguarion` attribute.</span></span>  
  
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
