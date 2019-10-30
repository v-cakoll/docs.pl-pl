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
# <a name="how-to-customize-a-time-based-cache-policy"></a>Instrukcje: Dostosowywanie zasad pamięci podręcznej na podstawie czasu

Podczas tworzenia zasad pamięci podręcznej opartej na czasie możesz dostosować zachowanie buforowania, określając wartości maksymalnego wieku, minimalnej Aktualności, maksymalnej wartości starej lub daty synchronizacji pamięci podręcznej. Obiekt <xref:System.Net.Cache.HttpRequestCachePolicy> zawiera kilka konstruktorów, które umożliwiają określenie prawidłowych kombinacji tych wartości.

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Aby utworzyć zasady pamięci podręcznej oparte na czasie, które używają daty synchronizacji pamięci podręcznej

Utwórz zasady pamięci podręcznej oparte na czasie, które używają daty synchronizacji pamięci podręcznej przez przekazanie obiektu <xref:System.DateTime> do konstruktora <xref:System.Net.Cache.HttpRequestCachePolicy>:

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

Dane wyjściowe są podobne do następujących:

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>Aby utworzyć zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnej wartości Aktualności

Utwórz zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnym świeżości przez określenie <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> jako wartości parametru `cacheAgeControl` i przekazanie obiektu <xref:System.TimeSpan> do konstruktora <xref:System.Net.Cache.HttpRequestCachePolicy>:

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

Dla następujących wywołań:

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

Dane wyjściowe:

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>Aby utworzyć zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnej wartości Aktualności i maksymalnym wieku

Utwórz zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnym okresie Aktualności i maksymalnym wieku przez określenie <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> jako wartości parametru `cacheAgeControl` i przekazanie dwóch <xref:System.TimeSpan> obiektów do konstruktora <xref:System.Net.Cache.HttpRequestCachePolicy>, jeden do określenia maksymalnego wieku zasobów i sekundy do Określ minimalną wartość świeżości dozwoloną dla obiektu zwróconego z pamięci podręcznej:

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

Dla następujących wywołań:
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

Dane wyjściowe:
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [\<element > requestCaching (Ustawienia sieci)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
