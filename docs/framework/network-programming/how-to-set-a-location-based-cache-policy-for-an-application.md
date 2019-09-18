---
title: 'Instrukcje: określanie zasad pamięci podręcznej na podstawie lokalizacji dla aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- explicitly defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: 150198c2bda220e4b37981e461e19b8e4e30e483
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048121"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="5ff12-102">Instrukcje: określanie zasad pamięci podręcznej na podstawie lokalizacji dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="5ff12-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="5ff12-103">Zasady pamięci podręcznej oparte na lokalizacji pozwalają aplikacji jawnie definiować zachowanie buforowania na podstawie lokalizacji żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="5ff12-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="5ff12-104">W tym temacie pokazano, jak skonfigurować zasady pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="5ff12-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="5ff12-105">Aby uzyskać informacje na temat ustawiania zasad dla aplikacji przy użyciu plików konfiguracji, zobacz [ \<requestCaching > element (Ustawienia sieci)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5ff12-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="5ff12-106">Aby ustawić zasady pamięci podręcznej oparte na lokalizacji dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="5ff12-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="5ff12-107">Utwórz obiekt <xref:System.Net.Cache.HttpRequestCachePolicy>lub. <xref:System.Net.Cache.RequestCachePolicy></span><span class="sxs-lookup"><span data-stu-id="5ff12-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="5ff12-108">Ustaw obiekt zasad jako domyślny dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5ff12-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="5ff12-109">Aby ustawić zasady, które pobierają żądane zasoby z pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="5ff12-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="5ff12-110">Utwórz zasady, które żądają żądanych zasobów z pamięci podręcznej, jeśli są dostępne, a w przeciwnym razie wysyła żądania do serwera, <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>ustawiając poziom pamięci podręcznej na.</span><span class="sxs-lookup"><span data-stu-id="5ff12-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="5ff12-111">Żądanie może być spełnione przez dowolną pamięć podręczną klienta i serwera, w tym zdalnych pamięci podręcznych.</span><span class="sxs-lookup"><span data-stu-id="5ff12-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="5ff12-112">Aby ustawić zasady, które uniemożliwiają dostarczenie zasobów przez żadną pamięć podręczną</span><span class="sxs-lookup"><span data-stu-id="5ff12-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="5ff12-113">Utwórz zasady, które uniemożliwiają każdej pamięci podręcznej dostarczenie żądanych zasobów przez ustawienie <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>poziomu pamięci podręcznej na wartość.</span><span class="sxs-lookup"><span data-stu-id="5ff12-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="5ff12-114">Ten poziom zasad usuwa zasób z lokalnej pamięci podręcznej, jeśli jest obecny, i wskazuje na zdalne pamięci podręczne, które powinny również usunąć zasób.</span><span class="sxs-lookup"><span data-stu-id="5ff12-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="5ff12-115">Aby ustawić zasady zwracające żądane zasoby tylko wtedy, gdy znajdują się w lokalnej pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="5ff12-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="5ff12-116">Utwórz zasady zwracające żądane zasoby tylko wtedy, gdy znajdują się w lokalnej pamięci podręcznej, ustawiając <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>poziom pamięci podręcznej na.</span><span class="sxs-lookup"><span data-stu-id="5ff12-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="5ff12-117">Jeśli żądany zasób nie znajduje się w pamięci podręcznej <xref:System.Net.WebException> , zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5ff12-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="5ff12-118">Aby ustawić zasady, które uniemożliwiają lokalnej pamięci podręcznej dostarczanie zasobów</span><span class="sxs-lookup"><span data-stu-id="5ff12-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="5ff12-119">Utwórz zasady, które uniemożliwiają lokalnej pamięci podręcznej dostarczenie żądanych zasobów przez ustawienie poziomu <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>pamięci podręcznej na wartość.</span><span class="sxs-lookup"><span data-stu-id="5ff12-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="5ff12-120">Jeśli żądany zasób znajduje się w pośredniej pamięci podręcznej i zostanie pomyślnie ponownie zweryfikowany, pośrednia pamięć podręczna może dostarczyć żądany zasób.</span><span class="sxs-lookup"><span data-stu-id="5ff12-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="5ff12-121">Aby ustawić zasady, które uniemożliwiają dostarczenie żądanych zasobów przez żadną pamięć podręczną</span><span class="sxs-lookup"><span data-stu-id="5ff12-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="5ff12-122">Utwórz zasady, które uniemożliwiają każdej pamięci podręcznej dostarczenie żądanych zasobów przez ustawienie <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>poziomu pamięci podręcznej na wartość.</span><span class="sxs-lookup"><span data-stu-id="5ff12-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="5ff12-123">Zasób zwrócony przez serwer może być przechowywany w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="5ff12-123">The resource returned by the server can be stored in the cache.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="5ff12-124">Aby ustawić zasady zezwalające każdej pamięci podręcznej na dostarczenie żądanych zasobów, jeśli zasób na serwerze nie jest nowszy niż w pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="5ff12-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="5ff12-125">Utwórz zasady, które zezwalają dowolnej pamięci podręcznej na dostarczenie żądanych zasobów, jeśli zasób na serwerze nie jest nowszy niż w pamięci podręcznej, ustawiając poziom bufora na <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span><span class="sxs-lookup"><span data-stu-id="5ff12-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ff12-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ff12-126">See also</span></span>

- [<span data-ttu-id="5ff12-127">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="5ff12-127">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="5ff12-128">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="5ff12-128">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="5ff12-129">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="5ff12-129">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="5ff12-130">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="5ff12-130">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="5ff12-131">\<requestCaching >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="5ff12-131">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
