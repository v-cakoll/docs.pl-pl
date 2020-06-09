---
title: 'Instrukcje: Wdrażanie serwera proxy odnajdywania'
ms.date: 03/30/2017
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
ms.openlocfilehash: ca7ab2ee434aef7649d71cbfc33273f48020788f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597075"
---
# <a name="how-to-implement-a-discovery-proxy"></a><span data-ttu-id="40b34-102">Instrukcje: Wdrażanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="40b34-102">How to: Implement a Discovery Proxy</span></span>

<span data-ttu-id="40b34-103">W tym temacie wyjaśniono, jak zaimplementować serwer proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="40b34-103">This topic explains how to implement a discovery proxy.</span></span> <span data-ttu-id="40b34-104">Aby uzyskać więcej informacji na temat funkcji odnajdywania w programie Windows Communication Foundation (WCF), zobacz [Omówienie odnajdywania WCF](wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="40b34-104">For more information about the discovery feature in Windows Communication Foundation (WCF), see [WCF Discovery Overview](wcf-discovery-overview.md).</span></span> <span data-ttu-id="40b34-105">Serwer proxy odnajdywania można zaimplementować przez utworzenie klasy rozszerzającej <xref:System.ServiceModel.Discovery.DiscoveryProxy> klasę abstrakcyjną.</span><span class="sxs-lookup"><span data-stu-id="40b34-105">A discovery proxy can be implemented by creating a class that extends the <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstract class.</span></span> <span data-ttu-id="40b34-106">Istnieje wiele innych klas pomocy technicznej zdefiniowanych i użytych w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="40b34-106">There are a number of other support classes defined and used in this sample.</span></span> <span data-ttu-id="40b34-107">`OnResolveAsyncResult`, `OnFindAsyncResult` i `AsyncResult` .</span><span class="sxs-lookup"><span data-stu-id="40b34-107">`OnResolveAsyncResult`, `OnFindAsyncResult`, and `AsyncResult`.</span></span> <span data-ttu-id="40b34-108">Te klasy implementują <xref:System.IAsyncResult> interfejs.</span><span class="sxs-lookup"><span data-stu-id="40b34-108">These classes implement the <xref:System.IAsyncResult> interface.</span></span> <span data-ttu-id="40b34-109">Aby uzyskać więcej informacji na temat <xref:System.IAsyncResult> [interfejsu system. IAsyncResult](xref:System.IAsyncResult).</span><span class="sxs-lookup"><span data-stu-id="40b34-109">For more information about <xref:System.IAsyncResult> see [System.IAsyncResult interface](xref:System.IAsyncResult).</span></span>

 <span data-ttu-id="40b34-110">Implementowanie serwera proxy odnajdywania jest podzielone na trzy główne części w tym temacie:</span><span class="sxs-lookup"><span data-stu-id="40b34-110">Implementing a discovery proxy is broken down into three main parts in this topic:</span></span>

- <span data-ttu-id="40b34-111">Zdefiniuj klasę zawierającą magazyn danych i rozszerza klasę abstrakcyjną <xref:System.ServiceModel.Discovery.DiscoveryProxy> .</span><span class="sxs-lookup"><span data-stu-id="40b34-111">Define a class that contains a data store and extends the abstract <xref:System.ServiceModel.Discovery.DiscoveryProxy> class.</span></span>

- <span data-ttu-id="40b34-112">Zaimplementuj klasę pomocnika `AsyncResult` .</span><span class="sxs-lookup"><span data-stu-id="40b34-112">Implement the helper `AsyncResult` class.</span></span>

- <span data-ttu-id="40b34-113">Hostowanie serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="40b34-113">Host the Discovery Proxy.</span></span>

### <a name="to-create-a-new-console-application-project"></a><span data-ttu-id="40b34-114">Aby utworzyć nowy projekt aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="40b34-114">To create a new console application project</span></span>

1. <span data-ttu-id="40b34-115">Uruchom program Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="40b34-115">Start Visual Studio 2012.</span></span>

2. <span data-ttu-id="40b34-116">Utwórz nowy projekt aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="40b34-116">Create a new console application project.</span></span> <span data-ttu-id="40b34-117">Nazwij projekt `DiscoveryProxy` i nadaj mu nazwę rozwiązanie `DiscoveryProxyExample` .</span><span class="sxs-lookup"><span data-stu-id="40b34-117">Name the project `DiscoveryProxy` and the name the solution `DiscoveryProxyExample`.</span></span>

3. <span data-ttu-id="40b34-118">Dodaj następujące odwołania do projektu</span><span class="sxs-lookup"><span data-stu-id="40b34-118">Add the following references to the project</span></span>

    1. <span data-ttu-id="40b34-119">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="40b34-119">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="40b34-120">System. ServiceModel. Discovery. dll</span><span class="sxs-lookup"><span data-stu-id="40b34-120">System.Servicemodel.Discovery.dll</span></span>

    > [!CAUTION]
    > <span data-ttu-id="40b34-121">Upewnij się, że Przywołujesz wersję 4,0 lub większą z tych zestawów.</span><span class="sxs-lookup"><span data-stu-id="40b34-121">Ensure that you reference version 4.0 or greater of these assemblies.</span></span>

### <a name="to-implement-the-proxydiscoveryservice-class"></a><span data-ttu-id="40b34-122">Aby zaimplementować klasę ProxyDiscoveryService</span><span class="sxs-lookup"><span data-stu-id="40b34-122">To implement the ProxyDiscoveryService class</span></span>

1. <span data-ttu-id="40b34-123">Dodaj nowy plik kodu do projektu i nadaj mu nazwę DiscoveryProxy.cs.</span><span class="sxs-lookup"><span data-stu-id="40b34-123">Add a new code file to your project and name it DiscoveryProxy.cs.</span></span>

2. <span data-ttu-id="40b34-124">Dodaj następujące `using` instrukcje do DiscoveryProxy.cs.</span><span class="sxs-lookup"><span data-stu-id="40b34-124">Add the following `using` statements to DiscoveryProxy.cs.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    using System.Xml;
    ```

3. <span data-ttu-id="40b34-125">Utwórz wartość `DiscoveryProxyService` z <xref:System.ServiceModel.Discovery.DiscoveryProxy> .</span><span class="sxs-lookup"><span data-stu-id="40b34-125">Derive the `DiscoveryProxyService` from <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span></span> <span data-ttu-id="40b34-126">Zastosuj `ServiceBehavior` atrybut do klasy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="40b34-126">Apply the `ServiceBehavior` attribute to the class as shown in the following example.</span></span>

    ```csharp
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
    }
    ```

4. <span data-ttu-id="40b34-127">Wewnątrz `DiscoveryProxy` klasy Zdefiniuj słownik do przechowywania zarejestrowanych usług.</span><span class="sxs-lookup"><span data-stu-id="40b34-127">Inside the `DiscoveryProxy` class define a dictionary to hold the registered services.</span></span>

    ```csharp
    // Repository to store EndpointDiscoveryMetadata.
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;
    ```

5. <span data-ttu-id="40b34-128">Zdefiniuj Konstruktor inicjujący słownik.</span><span class="sxs-lookup"><span data-stu-id="40b34-128">Define a constructor that initializes the dictionary.</span></span>

    ```csharp
    public DiscoveryProxyService()
            {
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
            }
    ```

### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a><span data-ttu-id="40b34-129">Aby zdefiniować metody służące do aktualizowania pamięci podręcznej serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="40b34-129">To define the methods used to update the discovery proxy cache</span></span>

1. <span data-ttu-id="40b34-130">Zaimplementuj `AddOnlineservice` metodę, aby dodać usługi do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="40b34-130">Implement the `AddOnlineservice` method to add services to the cache.</span></span> <span data-ttu-id="40b34-131">Ta wartość jest wywoływana za każdym razem, gdy serwer proxy odbiera komunikat anonsu.</span><span class="sxs-lookup"><span data-stu-id="40b34-131">This is called every time the proxy receives an announcement message.</span></span>

    ```csharp
    void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
    {
        lock (this.onlineServices)
        {
            this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
        }

        PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
    }
    ```

2. <span data-ttu-id="40b34-132">Zaimplementuj `RemoveOnlineService` metodę, która jest używana do usuwania usług z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="40b34-132">Implement the `RemoveOnlineService` method that is used to remove services from the cache.</span></span>

    ```csharp
    void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
    {
        if (endpointDiscoveryMetadata != null)
        {
            lock (this.onlineServices)
            {
                this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
        }
    }
    ```

3. <span data-ttu-id="40b34-133">Zaimplementuj `MatchFromOnlineService` metody, które próbują dopasować do usługi za pomocą usługi w słowniku.</span><span class="sxs-lookup"><span data-stu-id="40b34-133">Implement the `MatchFromOnlineService` methods that attempt to match a service with a service in the dictionary.</span></span>

    ```csharp
    void MatchFromOnlineService(FindRequestContext findRequestContext)
    {
        lock (this.onlineServices)
        {
            foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
            {
                if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                {
                    findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                }
            }
        }
    }
    ```

    ```csharp
    EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
    {
        EndpointDiscoveryMetadata matchingEndpoint = null;
        lock (this.onlineServices)
        {
            foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
            {
                if (criteria.Address == endpointDiscoveryMetadata.Address)
                {
                    matchingEndpoint = endpointDiscoveryMetadata;
                }
            }
        }
        return matchingEndpoint;
    }
    ```

4. <span data-ttu-id="40b34-134">Zaimplementuj `PrintDiscoveryMetadata` metodę, która udostępnia użytkownikowi dane wyjściowe z konsoli, co robi serwer proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="40b34-134">Implement the `PrintDiscoveryMetadata` method that provides the user with console text output of what the discovery proxy is doing.</span></span>

    ```csharp
    void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
    {
        Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
        foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
        {
            Console.WriteLine("** " + contractName.ToString());
            break;
        }
        Console.WriteLine("**** Operation Completed");
    }
    ```

5. <span data-ttu-id="40b34-135">Dodaj następujące klasy AsyncResult do DiscoveryProxyService.</span><span class="sxs-lookup"><span data-stu-id="40b34-135">Add the following AsyncResult classes to the DiscoveryProxyService.</span></span> <span data-ttu-id="40b34-136">Te klasy są używane do rozróżniania między różnymi wynikami operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="40b34-136">These classes are used to differentiate between the different asynchronous operation results.</span></span>

    ```csharp
    sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
    {
        public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
        }
    }

    sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
    {
        public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
        }
    }

    sealed class OnFindAsyncResult : AsyncResult
    {
        public OnFindAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnFindAsyncResult>(result);
        }
    }

    sealed class OnResolveAsyncResult : AsyncResult
    {
        EndpointDiscoveryMetadata matchingEndpoint;

        public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.matchingEndpoint = matchingEndpoint;
            this.Complete(true);
        }

        public static EndpointDiscoveryMetadata End(IAsyncResult result)
        {
            OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
            return thisPtr.matchingEndpoint;
        }
    }
    ```

### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a><span data-ttu-id="40b34-137">Aby zdefiniować metody implementujące funkcję serwera proxy odnajdowania</span><span class="sxs-lookup"><span data-stu-id="40b34-137">To define the methods that implement the discovery proxy functionality</span></span>

1. <span data-ttu-id="40b34-138">Zastąp <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="40b34-138">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="40b34-139">Ta metoda jest wywoływana, gdy serwer proxy odnajdywania odbiera komunikat anonsu online.</span><span class="sxs-lookup"><span data-stu-id="40b34-139">This method is called when the discovery proxy receives an online announcement message.</span></span>

    ```csharp
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
    protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
    {
        this.AddOnlineService(endpointDiscoveryMetadata);
        return new OnOnlineAnnouncementAsyncResult(callback, state);
    }
    ```

2. <span data-ttu-id="40b34-140">Zastąp <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="40b34-140">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="40b34-141">Ta metoda jest wywoływana, gdy serwer proxy odnajdywania zakończy przetwarzanie komunikatu anonsu.</span><span class="sxs-lookup"><span data-stu-id="40b34-141">This method is called when the discovery proxy finishes processing an announcement message.</span></span>

    ```csharp
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)
    {
        OnOnlineAnnouncementAsyncResult.End(result);
    }
    ```

3. <span data-ttu-id="40b34-142">Zastąp <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="40b34-142">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="40b34-143">Ta metoda jest wywoływana z serwerem proxy odnajdywania odbiera komunikat anonsu w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="40b34-143">This method is called with the discovery proxy receives an offline announcement message.</span></span>

    ```csharp
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
    protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
    {
        this.RemoveOnlineService(endpointDiscoveryMetadata);
        return new OnOfflineAnnouncementAsyncResult(callback, state);
    }
    ```

4. <span data-ttu-id="40b34-144">Zastąp <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="40b34-144">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="40b34-145">Ta metoda jest wywoływana, gdy serwer proxy odnajdywania zakończy przetwarzanie komunikatu anonsu w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="40b34-145">This method is called when the discovery proxy finishes processing an offline announcement message.</span></span>

    ```csharp
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)
    {
        OnOfflineAnnouncementAsyncResult.End(result);
    }
    ```

5. <span data-ttu-id="40b34-146">Zastąp <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="40b34-146">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="40b34-147">Ta metoda jest wywoływana, gdy serwer proxy odnajdywania odbiera żądanie find.</span><span class="sxs-lookup"><span data-stu-id="40b34-147">This method is called when the discovery proxy receives a find request.</span></span>

    ```csharp
    // OnBeginFind method is called when a Probe request message is received by the Proxy
    protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
    {
        this.MatchFromOnlineService(findRequestContext);
        return new OnFindAsyncResult(callback, state);
    }
    protected override IAsyncResult OnBeginFind(FindRequest findRequest, AsyncCallback callback, object state)
    {
        Collection<EndpointDiscoveryMetadata> matchingEndpoints = MatchFromCache(findRequest.Criteria);
        return new OnFindAsyncResult(
                    matchingEndpoints,
                    callback,
                    state);
    }
    ```

6. <span data-ttu-id="40b34-148">Zastąp <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="40b34-148">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="40b34-149">Ta metoda jest wywoływana, gdy serwer proxy odnajdywania zakończy przetwarzanie żądania find.</span><span class="sxs-lookup"><span data-stu-id="40b34-149">This method is called when the discovery proxy finishes processing a find request.</span></span>

    ```csharp
    protected override void OnEndFind(IAsyncResult result)
    {
        OnFindAsyncResult.End(result);
    }
    ```

7. <span data-ttu-id="40b34-150">Zastąp <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="40b34-150">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="40b34-151">Ta metoda jest wywoływana, gdy serwer proxy odnajdywania odbierze komunikat o rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="40b34-151">This method is called when the discovery proxy receives a resolve message.</span></span>

    ```csharp
    // OnBeginFind method is called when a Resolve request message is received by the Proxy
    protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
    }
    protected override IAsyncResult OnBeginResolve(ResolveRequest resolveRequest, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(
            this.proxy.MatchFromOnlineService(resolveRequest.Criteria),
            callback,
            state);
    }
    ```

8. <span data-ttu-id="40b34-152">Zastąp <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="40b34-152">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="40b34-153">Ta metoda jest wywoływana, gdy serwer proxy odnajdywania zakończy przetwarzanie komunikatu rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="40b34-153">This method is called when the discovery proxy finishes processing a resolve message.</span></span>

    ```csharp
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
    {
        return OnResolveAsyncResult.End(result);
    }
    ```

<span data-ttu-id="40b34-154">Onbegin..</span><span class="sxs-lookup"><span data-stu-id="40b34-154">The OnBegin..</span></span> <span data-ttu-id="40b34-155">/OnEnd..</span><span class="sxs-lookup"><span data-stu-id="40b34-155">/ OnEnd..</span></span> <span data-ttu-id="40b34-156">Metody zapewniają logikę dla kolejnych operacji odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="40b34-156">methods provide the logic for the subsequent discovery operations.</span></span> <span data-ttu-id="40b34-157">Na przykład <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> metody i <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> implementują Znajdowanie logiki dla serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="40b34-157">For example the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> and <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> methods implement the find logic for discovery proxy.</span></span> <span data-ttu-id="40b34-158">Gdy serwer proxy odnajdywania odbiera komunikat sondy, te metody są wykonywane w celu wysłania odpowiedzi z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="40b34-158">When the discovery proxy receives a probe message these methods are executed to send a response back to the client.</span></span> <span data-ttu-id="40b34-159">Możesz zmodyfikować logikę Znajdź zgodnie z potrzebami, na przykład można uwzględnić niestandardowe dopasowanie zakresu przez algorytmy lub analizę metadanych XML specyficzną dla aplikacji w ramach operacji znajdowania.</span><span class="sxs-lookup"><span data-stu-id="40b34-159">You may modify the find logic as you wish, for example you can incorporate custom scope matching by algorithms or application specific XML metadata parsing as part of your find operation.</span></span>

### <a name="to-implement-the-asyncresult-class"></a><span data-ttu-id="40b34-160">Aby zaimplementować klasę AsyncResult</span><span class="sxs-lookup"><span data-stu-id="40b34-160">To implement the AsyncResult class</span></span>

1. <span data-ttu-id="40b34-161">Zdefiniuj abstrakcyjną klasę podstawową klasy bazowej, która jest używana do wyprowadzania różnych asynchronicznych klas wynikowych.</span><span class="sxs-lookup"><span data-stu-id="40b34-161">Define the abstract base class AsyncResult which is used to derive the various async result classes.</span></span>

2. <span data-ttu-id="40b34-162">Utwórz nowy plik kodu o nazwie AsyncResult.cs.</span><span class="sxs-lookup"><span data-stu-id="40b34-162">Create a new code file called AsyncResult.cs.</span></span>

3. <span data-ttu-id="40b34-163">Dodaj następujące `using` instrukcje do AsyncResult.cs.</span><span class="sxs-lookup"><span data-stu-id="40b34-163">Add the following `using` statements to AsyncResult.cs.</span></span>

    ```csharp
    using System;
    using System.Threading;
    ```

4. <span data-ttu-id="40b34-164">Dodaj następującą klasę klasy AsyncResult.</span><span class="sxs-lookup"><span data-stu-id="40b34-164">Add the following AsyncResult class.</span></span>

    ```csharp
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    manualResetEvent ??= new ManualResetEvent(isCompleted);
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
    ```

### <a name="to-host-the-discoveryproxy"></a><span data-ttu-id="40b34-165">Aby hostować obiektu DiscoveryProxy</span><span class="sxs-lookup"><span data-stu-id="40b34-165">To host the DiscoveryProxy</span></span>

1. <span data-ttu-id="40b34-166">Otwórz plik Program.cs w projekcie DiscoveryProxyExample.</span><span class="sxs-lookup"><span data-stu-id="40b34-166">Open the Program.cs file in the DiscoveryProxyExample project.</span></span>

2. <span data-ttu-id="40b34-167">Dodaj następujące instrukcje `using`.</span><span class="sxs-lookup"><span data-stu-id="40b34-167">Add the following `using` statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="40b34-168">W `Main()` metodzie Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="40b34-168">Within the `Main()` method, add the following code.</span></span> <span data-ttu-id="40b34-169">Spowoduje to utworzenie wystąpienia `DiscoveryProxy` klasy.</span><span class="sxs-lookup"><span data-stu-id="40b34-169">This creates an instance of the `DiscoveryProxy` class.</span></span>

    ```csharp
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

    // Host the DiscoveryProxy service
    ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());
    ```

4. <span data-ttu-id="40b34-170">Następnie Dodaj następujący kod, aby dodać punkt końcowy odnajdywania i punkt końcowy anonsu.</span><span class="sxs-lookup"><span data-stu-id="40b34-170">Next add the following code to add a discovery endpoint and an announcement endpoint.</span></span>

    ```csharp
    try
    {
        // Add DiscoveryEndpoint to receive Probe and Resolve messages
        DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
        discoveryEndpoint.IsSystemEndpoint = false;

        // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
        AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

        proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
        proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

        proxyServiceHost.Open();

        Console.WriteLine("Proxy Service started.");
        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate the service.");
        Console.WriteLine();
        Console.ReadLine();

        proxyServiceHost.Close();
    }
    catch (CommunicationException e)
    {
        Console.WriteLine(e.Message);
    }
    catch (TimeoutException e)
    {
        Console.WriteLine(e.Message);
    }

    if (proxyServiceHost.State != CommunicationState.Closed)
    {
        Console.WriteLine("Aborting the service...");
        proxyServiceHost.Abort();
    }
    ```

<span data-ttu-id="40b34-171">Zakończono implementowanie serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="40b34-171">You have completed implementing the discovery proxy.</span></span> <span data-ttu-id="40b34-172">Przejdź do [: Implementowanie usługi wykrywalnej zarejestrowanej za pomocą serwera proxy odnajdywania](discoverable-service-that-registers-with-the-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="40b34-172">Continue on to [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](discoverable-service-that-registers-with-the-discovery-proxy.md).</span></span>

## <a name="example"></a><span data-ttu-id="40b34-173">Przykład</span><span class="sxs-lookup"><span data-stu-id="40b34-173">Example</span></span>

<span data-ttu-id="40b34-174">Jest to pełna lista kodów użytych w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="40b34-174">This is the full listing of the code used in this topic.</span></span>

```csharp
// DiscoveryProxy.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Collections.Generic;
using System.ServiceModel;
using System.ServiceModel.Discovery;
using System.Xml;

namespace Microsoft.Samples.Discovery
{
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
        // Repository to store EndpointDiscoveryMetadata. A database or a flat file could also be used instead.
        Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;

        public DiscoveryProxyService()
        {
            this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
        }

        // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
        protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.AddOnlineService(endpointDiscoveryMetadata);
            return new OnOnlineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOnlineAnnouncement(IAsyncResult result)
        {
            OnOnlineAnnouncementAsyncResult.End(result);
        }

        // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
        protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.RemoveOnlineService(endpointDiscoveryMetadata);
            return new OnOfflineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOfflineAnnouncement(IAsyncResult result)
        {
            OnOfflineAnnouncementAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Probe request message is received by the Proxy
        protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
        {
            this.MatchFromOnlineService(findRequestContext);
            return new OnFindAsyncResult(callback, state);
        }

        protected override void OnEndFind(IAsyncResult result)
        {
            OnFindAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Resolve request message is received by the Proxy
        protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
        {
            return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
        }

        protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
        {
            return OnResolveAsyncResult.End(result);
        }

        // The following are helper methods required by the Proxy implementation
        void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            lock (this.onlineServices)
            {
                this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
        }

        void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            if (endpointDiscoveryMetadata != null)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
            }
        }

        void MatchFromOnlineService(FindRequestContext findRequestContext)
        {
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                    {
                        findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                    }
                }
            }
        }

        EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
        {
            EndpointDiscoveryMetadata matchingEndpoint = null;
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (criteria.Address == endpointDiscoveryMetadata.Address)
                    {
                        matchingEndpoint = endpointDiscoveryMetadata;
                    }
                }
            }
            return matchingEndpoint;
        }

        void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
        {
            Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
            foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
            {
                Console.WriteLine("** " + contractName.ToString());
                break;
            }
            Console.WriteLine("**** Operation Completed");
        }

        sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
        {
            public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
        {
            public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnFindAsyncResult : AsyncResult
        {
            public OnFindAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnFindAsyncResult>(result);
            }
        }

        sealed class OnResolveAsyncResult : AsyncResult
        {
            EndpointDiscoveryMetadata matchingEndpoint;

            public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.matchingEndpoint = matchingEndpoint;
                this.Complete(true);
            }

            public static EndpointDiscoveryMetadata End(IAsyncResult result)
            {
                OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                return thisPtr.matchingEndpoint;
            }
        }
    }
}
```

```csharp
// AsyncResult.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Threading;

namespace Microsoft.Samples.Discovery
{
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    manualResetEvent ??= new ManualResetEvent(isCompleted);
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
}
```

```csharp
// program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            // Host the DiscoveryProxy service
            ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());

            try
            {
                // Add DiscoveryEndpoint to receive Probe and Resolve messages
                DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                discoveryEndpoint.IsSystemEndpoint = false;

                // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                proxyServiceHost.Open();

                Console.WriteLine("Proxy Service started.");
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                proxyServiceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (proxyServiceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                proxyServiceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="40b34-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40b34-175">See also</span></span>

- [<span data-ttu-id="40b34-176">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="40b34-176">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="40b34-177">Instrukcje: implementowanie odnajdywanej usługi rejestrowanej za pomocą serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="40b34-177">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="40b34-178">Instrukcje: wdrażanie aplikacji klienta znajdującej usługę przy użyciu serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="40b34-178">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
- [<span data-ttu-id="40b34-179">Instrukcje: testowanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="40b34-179">How to: Test the Discovery Proxy</span></span>](how-to-test-the-discovery-proxy.md)
