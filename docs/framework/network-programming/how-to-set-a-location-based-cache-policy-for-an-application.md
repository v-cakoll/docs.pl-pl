---
title: "Porady: Ustawianie zasad na podstawie lokalizacji pamięci podręcznej dla aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expliciting defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a145bf30930c9be81dc92f3a9f1eebda046b7e8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="5cb01-102">Porady: Ustawianie zasad na podstawie lokalizacji pamięci podręcznej dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="5cb01-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="5cb01-103">Zasady oparte na lokalizacji pamięci podręcznej zezwolić aplikacji na jawnie zdefiniuj zachowanie buforowania w oparciu o lokalizację żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="5cb01-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="5cb01-104">W tym temacie przedstawiono programowo ustawienie zasady pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="5cb01-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="5cb01-105">Aby uzyskać informacje na temat ustawiania zasad dla aplikacji za pomocą plików konfiguracji, zobacz [ \<requestCaching — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5cb01-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="5cb01-106">Aby ustawić zasady oparte na lokalizacji pamięci podręcznej dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="5cb01-106">To set a location-based cache policy for an application</span></span>  
  
1.  <span data-ttu-id="5cb01-107">Utwórz <xref:System.Net.Cache.RequestCachePolicy> lub <xref:System.Net.Cache.HttpRequestCachePolicy> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5cb01-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2.  <span data-ttu-id="5cb01-108">Ustaw ten obiekt zasad jako domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5cb01-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="5cb01-109">Aby ustawić zasady, które przyjmuje żądanych zasobów z pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="5cb01-109">To set a policy that takes requested resources from a cache</span></span>  
  
-   <span data-ttu-id="5cb01-110">Utwórz zasadę, która przyjmuje żądanych zasobów z pamięci podręcznej, jeśli jest dostępny, a w przeciwnym razie wysyła żądania do serwera, ustawiając poziomu do pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span><span class="sxs-lookup"><span data-stu-id="5cb01-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="5cb01-111">Żądania mogą być spełnione przez dowolnego pamięci podręcznej między klientem a serwerem, w tym zdalnego pamięci podręcznych.</span><span class="sxs-lookup"><span data-stu-id="5cb01-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="5cb01-112">Aby ustawić zasady, która uniemożliwia dostarczanie zasobów żadnych pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="5cb01-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
-   <span data-ttu-id="5cb01-113">Utwórz zasadę, która uniemożliwia dostarczanie żądanych zasobów przez ustawienie poziomu do pamięci podręcznej żadnych pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span><span class="sxs-lookup"><span data-stu-id="5cb01-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="5cb01-114">Ten poziom zasad Usuwa zasób z lokalnej pamięci podręcznej, jeśli jest obecny oraz wskazuje zdalnego pamięci podręcznych, czy należy również usunąć zasób.</span><span class="sxs-lookup"><span data-stu-id="5cb01-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="5cb01-115">Aby ustawić zasady, która zwraca żądanych zasobów tylko wtedy, gdy znajdują się w lokalnej pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="5cb01-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
-   <span data-ttu-id="5cb01-116">Utwórz zasadę, która zwraca żądanych zasobów tylko wtedy, gdy znajdują się w lokalnej pamięci podręcznej przez ustawienie poziomu do pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span><span class="sxs-lookup"><span data-stu-id="5cb01-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="5cb01-117">Jeśli żądany zasób nie jest w pamięci podręcznej, <xref:System.Net.WebException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5cb01-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="5cb01-118">Aby skonfigurować zasady, która uniemożliwia dostarczanie zasobów w lokalnej pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="5cb01-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
-   <span data-ttu-id="5cb01-119">Tworzenie zasad, który uniemożliwia dostarczanie żądanych zasobów przez ustawienie poziomu do pamięci podręcznej w lokalnej pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span><span class="sxs-lookup"><span data-stu-id="5cb01-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="5cb01-120">Żądany zasób w pośrednim pamięci podręcznej, jest pomyślnie ponownie sprawdzić poprawności pośredniego pamięci podręcznej można podać żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="5cb01-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="5cb01-121">Aby ustawić zasady, która uniemożliwia dostarczanie żadnych pamięci podręcznej zażądał zasobów</span><span class="sxs-lookup"><span data-stu-id="5cb01-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
-   <span data-ttu-id="5cb01-122">Utwórz zasadę, która uniemożliwia dostarczanie żądanych zasobów przez ustawienie poziomu do pamięci podręcznej żadnych pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span><span class="sxs-lookup"><span data-stu-id="5cb01-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="5cb01-123">Zasób zwrócony przez serwer mogą być przechowywane w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="5cb01-123">The resource returned by the server can be stored in the cache.</span></span>  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="5cb01-124">Aby ustawić zasady, które umożliwia żadnych pamięci podręcznej, aby dostarczyć żądanych zasobów, jeśli nie jest nowszy niż buforowanej kopii zasobu na serwerze</span><span class="sxs-lookup"><span data-stu-id="5cb01-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
-   <span data-ttu-id="5cb01-125">Utwórz zasadę, która umożliwia żadnych pamięci podręcznej, aby dostarczyć żądanych zasobów, jeśli zasobu na serwerze nie jest nowsza niż kopia pamięci podręcznej przez ustawienie poziomu do pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span><span class="sxs-lookup"><span data-stu-id="5cb01-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5cb01-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cb01-126">See Also</span></span>  
 [<span data-ttu-id="5cb01-127">Zarządzanie pamięci podręcznej dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="5cb01-127">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="5cb01-128">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="5cb01-128">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="5cb01-129">Zasady oparte na lokalizacji pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="5cb01-129">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="5cb01-130">Zasady na podstawie czasu pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="5cb01-130">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="5cb01-131">\<requestCaching — > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="5cb01-131">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
