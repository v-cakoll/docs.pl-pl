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
# <a name="how-to-customize-a-time-based-cache-policy"></a>Instrukcje: dostosowywanie zasad pamięci podręcznej na podstawie czasu

Podczas tworzenia zasad pamięci podręcznej opartych na czasie, można dostosować zachowanie buforowania, określając wartości dla maksymalnego wieku, minimalnej świeżości, maksymalnego nieaktualności lub daty synchronizacji pamięci podręcznej. Obiekt <xref:System.Net.Cache.HttpRequestCachePolicy> zawiera kilka konstruktorów, które umożliwiają określenie prawidłowych kombinacji tych wartości.

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Aby utworzyć zasadę pamięci podręcznej opartą na czasie, która używa daty synchronizacji pamięci podręcznej

Utwórz zasadę pamięci podręcznej opartą na czasie, <xref:System.DateTime> która <xref:System.Net.Cache.HttpRequestCachePolicy> używa daty synchronizacji pamięci podręcznej, przekazując obiekt do konstruktora:

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

Dane wyjściowe będą podobne do następujących:

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>Aby utworzyć zasadę pamięci podręcznej opartą na czasie, która opiera się na minimalnej świeżości

Utwórz zasadę pamięci podręcznej opartą na czasie, `cacheAgeControl` która jest oparta na minimalnej świeżości, określając jako wartość parametru i przekazując <xref:System.TimeSpan> <xref:System.Net.Cache.HttpRequestCachePolicy> <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> obiekt do konstruktora:

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

Dla następującego wywołania:

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

Dane wyjściowe wyglądają następująco:

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>Aby utworzyć zasadę pamięci podręcznej opartą na czasie, która opiera się na minimalnej świeżości i maksymalnym wieku

Utwórz zasadę pamięci podręcznej opartą na czasie, która <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> jest `cacheAgeControl` oparta na <xref:System.TimeSpan> minimalnej <xref:System.Net.Cache.HttpRequestCachePolicy> świeżości i maksymalnym wieku, określając jako wartość parametru i przekazując dwa obiekty do konstruktora, jeden, aby określić maksymalny wiek zasobów, a drugi, aby określić minimalną świeżość dozwoloną dla obiektu zwróconego z pamięci podręcznej:

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

Dla następującego wywołania:
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

Dane wyjściowe wyglądają następująco:
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [\<requestCaching> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
