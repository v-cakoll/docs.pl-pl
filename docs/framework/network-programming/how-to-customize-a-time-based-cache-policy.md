---
title: 'Instrukcje: Dostosowywanie zasad pamięci podręcznej na podstawie czasu'
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
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040631"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="4dfc7-102">Instrukcje: Dostosowywanie zasad pamięci podręcznej na podstawie czasu</span><span class="sxs-lookup"><span data-stu-id="4dfc7-102">How to: customize a time-based cache policy</span></span>

<span data-ttu-id="4dfc7-103">Podczas tworzenia zasad pamięci podręcznej opartej na czasie możesz dostosować zachowanie buforowania, określając wartości maksymalnego wieku, minimalnej Aktualności, maksymalnej wartości starej lub daty synchronizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="4dfc7-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="4dfc7-104">Obiekt <xref:System.Net.Cache.HttpRequestCachePolicy> zawiera kilka konstruktorów, które umożliwiają określenie prawidłowych kombinacji tych wartości.</span><span class="sxs-lookup"><span data-stu-id="4dfc7-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="4dfc7-105">Aby utworzyć zasady pamięci podręcznej oparte na czasie, które używają daty synchronizacji pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="4dfc7-105">To create a time-based cache policy that uses a cache synchronization date</span></span>

<span data-ttu-id="4dfc7-106">Utwórz zasady pamięci podręcznej oparte na czasie, które używają daty synchronizacji pamięci podręcznej przez przekazanie obiektu <xref:System.DateTime> do konstruktora <xref:System.Net.Cache.HttpRequestCachePolicy>:</span><span class="sxs-lookup"><span data-stu-id="4dfc7-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

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

<span data-ttu-id="4dfc7-107">Dane wyjściowe są podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="4dfc7-107">The output is similar to the following:</span></span>

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="4dfc7-108">Aby utworzyć zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnej wartości Aktualności</span><span class="sxs-lookup"><span data-stu-id="4dfc7-108">To create a time-based cache policy that is based on minimum freshness</span></span>

<span data-ttu-id="4dfc7-109">Utwórz zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnym świeżości przez określenie <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> jako wartości parametru `cacheAgeControl` i przekazanie obiektu <xref:System.TimeSpan> do konstruktora <xref:System.Net.Cache.HttpRequestCachePolicy>:</span><span class="sxs-lookup"><span data-stu-id="4dfc7-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

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

<span data-ttu-id="4dfc7-110">Dla następujących wywołań:</span><span class="sxs-lookup"><span data-stu-id="4dfc7-110">For the following invocation:</span></span>

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

<span data-ttu-id="4dfc7-111">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="4dfc7-111">The output is:</span></span>

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="4dfc7-112">Aby utworzyć zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnej wartości Aktualności i maksymalnym wieku</span><span class="sxs-lookup"><span data-stu-id="4dfc7-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>

<span data-ttu-id="4dfc7-113">Utwórz zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnym okresie Aktualności i maksymalnym wieku przez określenie <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> jako wartości parametru `cacheAgeControl` i przekazanie dwóch <xref:System.TimeSpan> obiektów do konstruktora <xref:System.Net.Cache.HttpRequestCachePolicy>, jeden do określenia maksymalnego wieku zasobów i sekundy do Określ minimalną wartość świeżości dozwoloną dla obiektu zwróconego z pamięci podręcznej:</span><span class="sxs-lookup"><span data-stu-id="4dfc7-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache:</span></span>

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

<span data-ttu-id="4dfc7-114">Dla następujących wywołań:</span><span class="sxs-lookup"><span data-stu-id="4dfc7-114">For the following invocation:</span></span>
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="4dfc7-115">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="4dfc7-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="4dfc7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4dfc7-116">See also</span></span>

- [<span data-ttu-id="4dfc7-117">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="4dfc7-117">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="4dfc7-118">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="4dfc7-118">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="4dfc7-119">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="4dfc7-119">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="4dfc7-120">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="4dfc7-120">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="4dfc7-121">\<element > requestCaching (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="4dfc7-121">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
