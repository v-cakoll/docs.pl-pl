---
title: 'Porady: Dostosowywanie zasad na podstawie czasu pamięci podręcznej'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fd2856ffcf6b21ba34771c231f608ad725b21763
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390968"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="356d6-102">Porady: Dostosowywanie zasad na podstawie czasu pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="356d6-102">How to: Customize a Time-Based Cache Policy</span></span>
<span data-ttu-id="356d6-103">Podczas tworzenia zasady na podstawie czasu pamięci podręcznej, można dostosować zachowanie buforowania, określając wartości maksymalny wiek, minimalna świeżości, maksymalna nieaktualności lub Data synchronizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="356d6-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="356d6-104"><xref:System.Net.Cache.HttpRequestCachePolicy> Obiektu zawiera kilka konstruktorów, które pozwalają określić prawidłową kombinację tych wartości.</span><span class="sxs-lookup"><span data-stu-id="356d6-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="356d6-105">Aby utworzyć zasady na podstawie czasu pamięci podręcznej, który używa Data synchronizacji pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="356d6-105">To create a time-based cache policy that uses a cache synchronization date</span></span>  
  
-   <span data-ttu-id="356d6-106">Utwórz zasadę na podstawie czasu pamięci podręcznej, która używa Data synchronizacji pamięci podręcznej przez przekazanie <xref:System.DateTime> do obiektu <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="356d6-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(when);  
        Console.WriteLine("When: {0}", when);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateLastSyncPolicy([when] As DateTime) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy([when])  
        Console.WriteLine("When: {0}", [when])  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 <span data-ttu-id="356d6-107">Wynik jest podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="356d6-107">The output is similar to the following:</span></span>  
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="356d6-108">Aby utworzyć zasady na podstawie czasu pamięci podręcznej, która jest oparta na minimalną świeżości</span><span class="sxs-lookup"><span data-stu-id="356d6-108">To create a time-based cache policy that is based on minimum freshness</span></span>  
  
-   <span data-ttu-id="356d6-109">Utwórz zasadę na podstawie czasu pamięci podręcznej, która jest oparta na minimalną świeżości, określając <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> jako `cacheAgeControl` wartość parametru i przekazywanie <xref:System.TimeSpan> do obiektu <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="356d6-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateMinFreshPolicy(span As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 <span data-ttu-id="356d6-110">Aby uzyskać następujące wywołanie:</span><span class="sxs-lookup"><span data-stu-id="356d6-110">For the following invocation:</span></span>  
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="356d6-111">Aby utworzyć zasady na podstawie czasu pamięci podręcznej, która na podstawie świeżości minimalny i maksymalny wiek</span><span class="sxs-lookup"><span data-stu-id="356d6-111">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>  
  
-   <span data-ttu-id="356d6-112">Utwórz zasadę na podstawie czasu pamięci podręcznej, która na podstawie świeżości minimalny i maksymalny wiek, określając <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> jako `cacheAgeControl` wartość parametru i przekazywanie dwa <xref:System.TimeSpan> obiekty do <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktora, aby określić okres ważności zasoby oraz określ minimalną świeżości drugiego dozwolony dla obiektu zwróconego z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="356d6-112">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)  
    {  
        HttpRequestCachePolicy policy =   
        new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateFreshAndAgePolicy(freshMinimum As TimeSpan, ageMaximum As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 <span data-ttu-id="356d6-113">Aby uzyskać następujące wywołanie:</span><span class="sxs-lookup"><span data-stu-id="356d6-113">For the following invocation:</span></span>  
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="356d6-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="356d6-114">See Also</span></span>  
 [<span data-ttu-id="356d6-115">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="356d6-115">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="356d6-116">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="356d6-116">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="356d6-117">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="356d6-117">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="356d6-118">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="356d6-118">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="356d6-119">\<requestCaching — > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="356d6-119">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
