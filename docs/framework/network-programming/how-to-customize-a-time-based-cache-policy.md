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
ms.openlocfilehash: c28c6daf9b873a19291b1636112eae6546412be2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048313"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="0dfeb-102">Instrukcje: dostosowywanie zasad pamięci podręcznej na podstawie czasu</span><span class="sxs-lookup"><span data-stu-id="0dfeb-102">How to: Customize a Time-Based Cache Policy</span></span>
<span data-ttu-id="0dfeb-103">Podczas tworzenia zasad pamięci podręcznej opartej na czasie możesz dostosować zachowanie buforowania, określając wartości maksymalnego wieku, minimalnej Aktualności, maksymalnej wartości starej lub daty synchronizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="0dfeb-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="0dfeb-104"><xref:System.Net.Cache.HttpRequestCachePolicy> Obiekt zawiera kilka konstruktorów, które umożliwiają określenie prawidłowych kombinacji tych wartości.</span><span class="sxs-lookup"><span data-stu-id="0dfeb-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="0dfeb-105">Aby utworzyć zasady pamięci podręcznej oparte na czasie, które używają daty synchronizacji pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="0dfeb-105">To create a time-based cache policy that uses a cache synchronization date</span></span>  
  
- <span data-ttu-id="0dfeb-106">Utwórz zasady pamięci podręcznej oparte na czasie, które używają daty synchronizacji pamięci podręcznej przez <xref:System.Net.Cache.HttpRequestCachePolicy> przekazanie <xref:System.DateTime> obiektu do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0dfeb-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
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
  
 <span data-ttu-id="0dfeb-107">Dane wyjściowe są podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="0dfeb-107">The output is similar to the following:</span></span>  
  
```output
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="0dfeb-108">Aby utworzyć zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnej wartości Aktualności</span><span class="sxs-lookup"><span data-stu-id="0dfeb-108">To create a time-based cache policy that is based on minimum freshness</span></span>  
  
- <span data-ttu-id="0dfeb-109">Utwórz zasady pamięci podręcznej oparte na czasie, które są oparte na minimalnym <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> świeżości `cacheAgeControl` przez określenie wartości <xref:System.TimeSpan> parametru i <xref:System.Net.Cache.HttpRequestCachePolicy> przekazanie obiektu do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0dfeb-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
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
  
 <span data-ttu-id="0dfeb-110">Dla następujących wywołań:</span><span class="sxs-lookup"><span data-stu-id="0dfeb-110">For the following invocation:</span></span>  
  
```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  

 <span data-ttu-id="0dfeb-111">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0dfeb-111">The output is:</span></span>
  
```output
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="0dfeb-112">Aby utworzyć zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnej wartości Aktualności i maksymalnym wieku</span><span class="sxs-lookup"><span data-stu-id="0dfeb-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>  
  
- <span data-ttu-id="0dfeb-113">Utwórz zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnym okresie Aktualności <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> i maksymalnym wieku, określając `cacheAgeControl` jako <xref:System.TimeSpan> wartość parametru i <xref:System.Net.Cache.HttpRequestCachePolicy> przekazując dwa obiekty do konstruktora, jeden w celu określenia maksymalnego wieku dla zasoby i sekundę, aby określić minimalną wartość świeżości dozwoloną dla obiektu zwróconego z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="0dfeb-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache.</span></span>  
  
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
  
 <span data-ttu-id="0dfeb-114">Dla następujących wywołań:</span><span class="sxs-lookup"><span data-stu-id="0dfeb-114">For the following invocation:</span></span>  
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="0dfeb-115">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0dfeb-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="0dfeb-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0dfeb-116">See also</span></span>

- [<span data-ttu-id="0dfeb-117">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="0dfeb-117">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="0dfeb-118">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="0dfeb-118">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="0dfeb-119">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="0dfeb-119">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="0dfeb-120">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="0dfeb-120">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="0dfeb-121">\<requestCaching >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="0dfeb-121">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
