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
# <a name="how-to-customize-a-time-based-cache-policy"></a>Instrukcje: dostosowywanie zasad pamięci podręcznej na podstawie czasu
Podczas tworzenia zasad pamięci podręcznej opartej na czasie możesz dostosować zachowanie buforowania, określając wartości maksymalnego wieku, minimalnej Aktualności, maksymalnej wartości starej lub daty synchronizacji pamięci podręcznej. <xref:System.Net.Cache.HttpRequestCachePolicy> Obiekt zawiera kilka konstruktorów, które umożliwiają określenie prawidłowych kombinacji tych wartości.  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Aby utworzyć zasady pamięci podręcznej oparte na czasie, które używają daty synchronizacji pamięci podręcznej  
  
- Utwórz zasady pamięci podręcznej oparte na czasie, które używają daty synchronizacji pamięci podręcznej przez <xref:System.Net.Cache.HttpRequestCachePolicy> przekazanie <xref:System.DateTime> obiektu do konstruktora.  
  
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
  
 Dane wyjściowe są podobne do następujących:  
  
```output
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>Aby utworzyć zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnej wartości Aktualności  
  
- Utwórz zasady pamięci podręcznej oparte na czasie, które są oparte na minimalnym <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> świeżości `cacheAgeControl` przez określenie wartości <xref:System.TimeSpan> parametru i <xref:System.Net.Cache.HttpRequestCachePolicy> przekazanie obiektu do konstruktora.  
  
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
  
 Dla następujących wywołań:  
  
```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  

 Dane wyjściowe:
  
```output
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>Aby utworzyć zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnej wartości Aktualności i maksymalnym wieku  
  
- Utwórz zasady pamięci podręcznej oparte na czasie, które opierają się na minimalnym okresie Aktualności <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> i maksymalnym wieku, określając `cacheAgeControl` jako <xref:System.TimeSpan> wartość parametru i <xref:System.Net.Cache.HttpRequestCachePolicy> przekazując dwa obiekty do konstruktora, jeden w celu określenia maksymalnego wieku dla zasoby i sekundę, aby określić minimalną wartość świeżości dozwoloną dla obiektu zwróconego z pamięci podręcznej.  
  
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
- [\<requestCaching >, element (Ustawienia sieci)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
