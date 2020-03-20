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
ms.openlocfilehash: 6fe569e781b005461ea41e3d6b90859666f9601a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180780"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="d0f91-102">Instrukcje: określanie zasad pamięci podręcznej na podstawie lokalizacji dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="d0f91-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="d0f91-103">Zasady pamięci podręcznej oparte na lokalizacji umożliwiają aplikacji jawne definiowanie zachowania buforowania na podstawie lokalizacji żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="d0f91-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="d0f91-104">W tym temacie przedstawiono programowe ustawianie zasad pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d0f91-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="d0f91-105">Aby uzyskać informacje na temat ustawiania zasad dla aplikacji przy użyciu plików konfiguracyjnych, zobacz [ \<requestCaching> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="d0f91-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="d0f91-106">Aby ustawić zasadę pamięci podręcznej opartą na lokalizacji dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="d0f91-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="d0f91-107">Utwórz <xref:System.Net.Cache.RequestCachePolicy> <xref:System.Net.Cache.HttpRequestCachePolicy> obiekt lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="d0f91-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="d0f91-108">Ustaw obiekt zasad jako domyślny dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0f91-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="d0f91-109">Aby ustawić zasadę, która pobiera żądane zasoby z pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="d0f91-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="d0f91-110">Utwórz zasadę, która pobiera żądane zasoby z pamięci podręcznej, jeśli są dostępne, a w przeciwnym razie wysyła żądania do serwera, ustawiając poziom pamięci podręcznej na <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span><span class="sxs-lookup"><span data-stu-id="d0f91-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="d0f91-111">Żądanie może zostać spełnione przez dowolną pamięć podręczną między klientem a serwerem, w tym zdalne pamięci podręczne.</span><span class="sxs-lookup"><span data-stu-id="d0f91-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="d0f91-112">Aby ustawić zasadę, która uniemożliwia dostarczanie zasobów przez pamięć podręczną</span><span class="sxs-lookup"><span data-stu-id="d0f91-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="d0f91-113">Utwórz zasadę, która uniemożliwia dostarczanie żądanych zasobów przez <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>pamięć podręczną, ustawiając poziom pamięci podręcznej na .</span><span class="sxs-lookup"><span data-stu-id="d0f91-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="d0f91-114">Ten poziom zasad usuwa zasób z lokalnej pamięci podręcznej, jeśli jest obecny i wskazuje do zdalnych pamięci podręcznych, że należy również usunąć zasób.</span><span class="sxs-lookup"><span data-stu-id="d0f91-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="d0f91-115">Aby ustawić zasadę, która zwraca żądane zasoby tylko wtedy, gdy znajdują się one w lokalnej pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="d0f91-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="d0f91-116">Utwórz zasadę, która zwraca żądane zasoby tylko wtedy, gdy <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>znajdują się w lokalnej pamięci podręcznej, ustawiając poziom pamięci podręcznej na .</span><span class="sxs-lookup"><span data-stu-id="d0f91-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="d0f91-117">Jeśli żądany zasób nie znajduje <xref:System.Net.WebException> się w pamięci podręcznej, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d0f91-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="d0f91-118">Aby ustawić zasadę uniemożliwiającą lokalnej pamięci podręcznej dostarczanie zasobów</span><span class="sxs-lookup"><span data-stu-id="d0f91-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="d0f91-119">Utwórz zasadę, która uniemożliwia lokalnej pamięci podręcznej dostarczanie żądanych zasobów, ustawiając poziom pamięci podręcznej na <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span><span class="sxs-lookup"><span data-stu-id="d0f91-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="d0f91-120">Jeśli żądany zasób znajduje się w pośredniej pamięci podręcznej i zostanie pomyślnie ponownie zweryfikowany, pośrednia pamięć podręczna może dostarczyć żądany zasób.</span><span class="sxs-lookup"><span data-stu-id="d0f91-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="d0f91-121">Aby ustawić zasadę uniemożliwiającą dostarczanie żądanych zasobów przez pamięć podręczną</span><span class="sxs-lookup"><span data-stu-id="d0f91-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="d0f91-122">Utwórz zasadę, która uniemożliwia dostarczanie żądanych zasobów przez <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>pamięć podręczną, ustawiając poziom pamięci podręcznej na .</span><span class="sxs-lookup"><span data-stu-id="d0f91-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="d0f91-123">Zasób zwracany przez serwer może być przechowywany w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d0f91-123">The resource returned by the server can be stored in the cache.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="d0f91-124">Aby ustawić zasadę, która umożliwia dowolnej pamięci podręcznej dostarczanie żądanych zasobów, jeśli zasób na serwerze nie jest nowszy niż kopia buforowana</span><span class="sxs-lookup"><span data-stu-id="d0f91-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="d0f91-125">Utwórz zasadę, która umożliwia każdej pamięci podręcznej dostarczanie żądanych zasobów, jeśli zasób na <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>serwerze nie jest nowszy niż kopia buforowana, ustawiając poziom pamięci podręcznej na .</span><span class="sxs-lookup"><span data-stu-id="d0f91-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0f91-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0f91-126">See also</span></span>

- [<span data-ttu-id="d0f91-127">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="d0f91-127">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="d0f91-128">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="d0f91-128">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="d0f91-129">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="d0f91-129">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="d0f91-130">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="d0f91-130">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="d0f91-131">\<requestCaching> Element (Ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="d0f91-131">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
