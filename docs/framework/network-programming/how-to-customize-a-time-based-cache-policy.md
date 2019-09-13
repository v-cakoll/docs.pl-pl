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
ms.openlocfilehash: 5df070bb2cfef42d60247cad39f2a2f76963bae8
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894744"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="73086-102">Instrukcje: dostosowywanie zasad pamięci podręcznej na podstawie czasu</span><span class="sxs-lookup"><span data-stu-id="73086-102">How to: Customize a Time-Based Cache Policy</span></span>
<span data-ttu-id="73086-103">Podczas tworzenia zasad pamięci podręcznej opartej na czasie możesz dostosować zachowanie buforowania, określając wartości maksymalnego wieku, minimalnej Aktualności, maksymalnej wartości starej lub daty synchronizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="73086-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="73086-104"><xref:System.Net.Cache.HttpRequestCachePolicy> Obiekt zawiera kilka konstruktorów, które umożliwiają określenie prawidłowych kombinacji tych wartości.</span><span class="sxs-lookup"><span data-stu-id="73086-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="73086-105">Aby utworzyć zasady pamięci podręcznej oparte na czasie, które używają daty synchronizacji pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="73086-105">To create a time-based cache policy that uses a cache synchronization date</span></span>  
  
- <span data-ttu-id="73086-106">Utwórz zasady pamięci podręcznej oparte na czasie, które używają daty synchronizacji pamięci podręcznej przez <xref:System.Net.Cache.HttpRequestCachePolicy> przekazanie <xref:System.DateTime> obiektu do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="73086-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
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
  
 <span data-ttu-id="73086-107">Dane wyjściowe są podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="73086-107">The output is similar to the following:</span></span>  
  
```output
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="73086-108">Aby utworzyć zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnej wartości Aktualności</span><span class="sxs-lookup"><span data-stu-id="73086-108">To create a time-based cache policy that is based on minimum freshness</span></span>  
  
- <span data-ttu-id="73086-109">Utwórz zasady pamięci podręcznej oparte na czasie, które są oparte na minimalnym <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> świeżości `cacheAgeControl` przez określenie wartości <xref:System.TimeSpan> parametru i <xref:System.Net.Cache.HttpRequestCachePolicy> przekazanie obiektu do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="73086-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
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
  
 <span data-ttu-id="73086-110">Dla następujących wywołań:</span><span class="sxs-lookup"><span data-stu-id="73086-110">For the following invocation:</span></span>  
  
```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  

 <span data-ttu-id="73086-111">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="73086-111">The output is:</span></span>
  
```output
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="73086-112">Aby utworzyć zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnej wartości Aktualności i maksymalnym wieku</span><span class="sxs-lookup"><span data-stu-id="73086-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>  
  
- <span data-ttu-id="73086-113">Utwórz zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnym okresie Aktualności <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> i maksymalnym wieku, określając `cacheAgeControl` jako <xref:System.TimeSpan> wartość parametru i <xref:System.Net.Cache.HttpRequestCachePolicy> przekazując dwa obiekty do konstruktora, jeden w celu określenia maksymalnego wieku dla zasoby i sekundę, aby określić minimalną wartość świeżości dozwoloną dla obiektu zwróconego z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="73086-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache.</span></span>  
  
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
  
 <span data-ttu-id="73086-114">Dla następujących wywołań:</span><span class="sxs-lookup"><span data-stu-id="73086-114">For the following invocation:</span></span>  
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="73086-115">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="73086-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="73086-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73086-116">See also</span></span>

- [<span data-ttu-id="73086-117">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="73086-117">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="73086-118">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="73086-118">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="73086-119">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="73086-119">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="73086-120">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="73086-120">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="73086-121">\<requestCaching >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="73086-121">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
