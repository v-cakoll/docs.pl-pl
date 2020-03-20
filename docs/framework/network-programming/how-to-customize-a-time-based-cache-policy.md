---
title: 'Instrukcje: dostosowywanie zasad pamięci podręcznej na podstawie czasu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: 1a2ba404e333eeec2a23758c834876d0df5aba81
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040631"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="46e64-102">Instrukcje: dostosowywanie zasad pamięci podręcznej na podstawie czasu</span><span class="sxs-lookup"><span data-stu-id="46e64-102">How to: customize a time-based cache policy</span></span>

<span data-ttu-id="46e64-103">Podczas tworzenia zasad pamięci podręcznej opartych na czasie, można dostosować zachowanie buforowania, określając wartości dla maksymalnego wieku, minimalnej świeżości, maksymalnego nieaktualności lub daty synchronizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="46e64-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="46e64-104">Obiekt <xref:System.Net.Cache.HttpRequestCachePolicy> zawiera kilka konstruktorów, które umożliwiają określenie prawidłowych kombinacji tych wartości.</span><span class="sxs-lookup"><span data-stu-id="46e64-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="46e64-105">Aby utworzyć zasadę pamięci podręcznej opartą na czasie, która używa daty synchronizacji pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="46e64-105">To create a time-based cache policy that uses a cache synchronization date</span></span>

<span data-ttu-id="46e64-106">Utwórz zasadę pamięci podręcznej opartą na czasie, <xref:System.DateTime> która <xref:System.Net.Cache.HttpRequestCachePolicy> używa daty synchronizacji pamięci podręcznej, przekazując obiekt do konstruktora:</span><span class="sxs-lookup"><span data-stu-id="46e64-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)
{
    var policy = new HttpRequestCachePolicy(when);
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

<span data-ttu-id="46e64-107">Dane wyjściowe będą podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="46e64-107">The output is similar to the following:</span></span>

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="46e64-108">Aby utworzyć zasadę pamięci podręcznej opartą na czasie, która opiera się na minimalnej świeżości</span><span class="sxs-lookup"><span data-stu-id="46e64-108">To create a time-based cache policy that is based on minimum freshness</span></span>

<span data-ttu-id="46e64-109">Utwórz zasadę pamięci podręcznej opartą na czasie, `cacheAgeControl` która jest oparta na minimalnej świeżości, określając jako wartość parametru i przekazując <xref:System.TimeSpan> <xref:System.Net.Cache.HttpRequestCachePolicy> <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> obiekt do konstruktora:</span><span class="sxs-lookup"><span data-stu-id="46e64-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);
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

<span data-ttu-id="46e64-110">Dla następującego wywołania:</span><span class="sxs-lookup"><span data-stu-id="46e64-110">For the following invocation:</span></span>

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

<span data-ttu-id="46e64-111">Dane wyjściowe wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="46e64-111">The output is:</span></span>

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="46e64-112">Aby utworzyć zasadę pamięci podręcznej opartą na czasie, która opiera się na minimalnej świeżości i maksymalnym wieku</span><span class="sxs-lookup"><span data-stu-id="46e64-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>

<span data-ttu-id="46e64-113">Utwórz zasadę pamięci podręcznej opartą na czasie, która <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> jest `cacheAgeControl` oparta na <xref:System.TimeSpan> minimalnej <xref:System.Net.Cache.HttpRequestCachePolicy> świeżości i maksymalnym wieku, określając jako wartość parametru i przekazując dwa obiekty do konstruktora, jeden, aby określić maksymalny wiek zasobów, a drugi, aby określić minimalną świeżość dozwoloną dla obiektu zwróconego z pamięci podręcznej:</span><span class="sxs-lookup"><span data-stu-id="46e64-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache:</span></span>

```csharp
public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);
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

<span data-ttu-id="46e64-114">Dla następującego wywołania:</span><span class="sxs-lookup"><span data-stu-id="46e64-114">For the following invocation:</span></span>
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="46e64-115">Dane wyjściowe wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="46e64-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="46e64-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46e64-116">See also</span></span>

- [<span data-ttu-id="46e64-117">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="46e64-117">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="46e64-118">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="46e64-118">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="46e64-119">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="46e64-119">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="46e64-120">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="46e64-120">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="46e64-121">\<requestCaching> Element (Ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="46e64-121">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
